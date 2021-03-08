# Instrucciones para mantenedores
### Instrucciones de compilacion
#### Dependencias
##### NodeJS 12 o posterior
##### NPM
##### Git
#### Compilaciones Linux
#### Sistema operativo minimo requerido: Ubuntu, Fedora, Arch, Manjaro o derivadas
#### Sistema operativo recomendado: Ubuntu 20.04 LTS o Ubuntu 20.10, Fedora 33
~~~
git clone https://github.com/TechAppsSv/iconny.git
~~~
~~~
cd iconny
~~~
~~~
npm i o npm install 
~~~
~~~
npm run build-linux
~~~
#### Compilaciones Windows (.exe)
#### Sistema operativo minimo requerido: Windows 10 
#### Sistema operativo recomendado: Windows 10
~~~
git clone https://github.com/TechAppsSv/iconny.git
~~~
~~~
cd iconny
~~~
~~~
npm i o npm install 
~~~
~~~
npm run build-win
~~~
#### Sistema operativo minimo requerido: MacOs Catalina
#### Sistema operativo recomendado: MacOs Catalina
~~~
git clone https://github.com/TechAppsSv/iconny.git
~~~
~~~
cd iconny
~~~
~~~
npm i o npm install 
~~~
~~~
npm run build-mac
~~~
## Cambiar formatos de los binarios
## Dirigase al package.json
#### Deberia de ver algo asi
~~~
{
	"name": "iconny",
	"productName": "Iconny Browser Linux ",
	"version": "1.0.4",
	"description": "Maxima rapidez y ligereza",
	"main": "src/wdk/wdk-init-webvi/index.js",
	"scripts": {
		"pack": "build --dir",
		"dist": "build",
		"build-linux": "electron-builder --linux --publish always",
		"build-win": "electron-builder --win --publish always",
		"build-mac": "electron-builder --mac --publish always",
		"start": "electron src/wdk/wdk-init-webvi/index.js"
	},
	"author": "Iconny <techappsv@hotmail.com>",
	"license": "MIT",
	"build": {
		"appId": "com.techapps.iconny",
		"productName": "Iconny Browser Linux",
		"win": {
			"target": [
				"nsis",
				"zip"
			],
			"icon": "build/icon.ico"
		},
		"mac": {
			"category": "productivity",
			"target": [
				"pkg"
			],
			"icon": "build/icon.icns"
		},
		"linux": {
			"category": "Browser",
			"target": [
				"snap"
			],
			"icon": "build/background.png"
		},
		"publish": [
			{
				"provider": "generic",
				"url": "https://gitlab.com"
			}
		],
		"nsis": {
			"oneClick": "false",
			"allowToChangeInstallationDirectory": "true",
			"perMachine": "true"
		}
	},
	"dependencies": {
		"@cliqz/adblocker-electron": "^1.20.3",
		"cross-fetch": "^3.0.6",
		"electron-context-menu": "^0.9.1",
		"electron-navigation": "^1.5.8",
		"electron-navigation-iconny": "^1.5.8",
		"node-fetch": "^2.6.1"
	},
	"devDependencies": {
		"electron": "^11.3.0",
		"electron-builder": "^22.6.1",
		"electron-devtools-installer": "^3.1.1"
	}
}

~~~

#### Modificar estas secciones cambiando la palabra que esta en ""
~~~
{
	"name": "iconny",
	"productName": "Iconny Browser Linux ",
	"version": "1.0.4",
	"description": "Maxima rapidez y ligereza",
	"main": "src/wdk/wdk-init-webvi/index.js",
	"scripts": {
		"pack": "build --dir",
		"dist": "build",
		"build-linux": "electron-builder --linux --publish always",
		"build-win": "electron-builder --win --publish always",
		"build-mac": "electron-builder --mac --publish always",
		"start": "electron src/wdk/wdk-init-webvi/index.js"
	},
	"author": "Iconny <techappsv@hotmail.com>",
	"license": "MIT",
	"build": {
		"appId": "com.techapps.iconny",
		"productName": "Iconny Browser Linux",
		"win": {
			"target": [
				"nsis",  <------ Puede ser cambiado por : .msi
				"zip"
			],
			"icon": "build/icon.ico" 
		},
		"mac": {
			"category": "productivity",
			"target": [
				"pkg"  <------ Puede ser cambiado por: .dmg
			],
			"icon": "build/icon.icns"
		},
		"linux": {
			"category": "Browser",
			"target": [
				"snap" <------ Puede ser cambiado por : .deb, .rpm, 
                               .AppImage, .tar.gz, .pacman (No flatpak)
			],
			"icon": "build/background.png"
		},
		"publish": [
			{
				"provider": "generic",
				"url": "https://gitlab.com"
			}
		],
		"nsis": {
			"oneClick": "false",
			"allowToChangeInstallationDirectory": "true",
			"perMachine": "true"
		}
	},
	"dependencies": {
		"@cliqz/adblocker-electron": "^1.20.3",
		"cross-fetch": "^3.0.6",
		"electron-context-menu": "^0.9.1",
		"electron-navigation": "^1.5.8",
		"electron-navigation-iconny": "^1.5.8",
		"node-fetch": "^2.6.1"
	},
	"devDependencies": {
		"electron": "^11.3.0",
		"electron-builder": "^22.6.1",
		"electron-devtools-installer": "^3.1.1"
	}
}


~~~
### Instrucciones para subir binario mediante un pull request
#### Puede ver el ejemplo  ubicada en la carpeta example 
## ADVERTENCIA NO SUBIR BINARIO AL REPOSITORIO SOLAMENTE EL README.MD  Y EL CODIGO MODIFICADO
#### 1.Subir el codigo con las modificaciones hechas
#### 2.Subir un README.MD con los siguientes datos:
##### Nombre de mantenedor
##### Version compilada
##### Formato compilado
##### Rama de la version compilada
##### En que distrubucion fue probada
##### Link del repositorio o link de descarga
### EJEMPLO:
  ~~~ 
  # Iconny Community 
  ### Mantenido por : INSERTE SU NOMBRE DE GITHUB
  ### Version Compilada: 12
  ### Rama: Stable
  ### Distrubucion probada: Debian 10 Buster Stable(Non-free)
  ### Formato: .deb
  ### Descarga: https//:github.com/iconny.deb

~~~
## Posibles errores

### 1. ERROR 404 - Not found electron-navigation-iconny
~~~
npm ERR! code E404
npm ERR! 404 Not Found - GET https://registry.npmjs.org/electron-navigation-iconny - Not found
npm ERR! 404 
npm ERR! 404  'electron-navigation-iconny@^1.5.8' is not in the npm registry.
npm ERR! 404 You should bug the author to publish it (or use the name yourself!)
npm ERR! 404 
npm ERR! 404 Note that you can also install from a
npm ERR! 404 tarball, folder, http url, or git url.

npm ERR! A complete log of this run can be found in:
npm ERR!     /home/user/.npm/_logs/2021-03-08T16_37_19_611Z-debug.log
~~~
### Solucion:
#### Este modulo es un fork de electron-navigation hecho para el modo perfil secundario y que separe las sesiones  este no se encuentra en los repositorios de npm entonces debe de ser descargados e instalados manualmente
#
#### Clonar el repositorio 
~~~
git clone https://github.com/TechAppsSv/iconny-navigation.git
~~~
#
#### Eliminar la siguiente linea del package.json
~~~
"electron-navigation-iconny": "^1.5.8",
~~~
#
#### Volver a ejecutar 
~~~
npm i
~~~
#
#### Mover carpeta descargada  a la carpeta node_modules
#
#### Volver a poner la linea eliminada del package.json
~~~
"electron-navigation-iconny": "^1.5.8",
~~~
#
# 2. Al ejecutar en modo desarrollo con el comando "npm start" no se ve igual la interfaz
#
#### Esto sucede porque el modulo electron-navigation en las compilaciones oficiales esta modificado para mejorar la experiencia del usuario en funcionamiento y interfaz
#
### Solucion
#
#### Clonar el repositorio
~~~
git clone https://github.com/TechAppsSv/iconny-navigation-mod.git
~~~
#
#### Eliminar la carpeta electron-navigation de la carpeta node_modules
#
#### Mover carpeta descargada a la carpeta node_modules 
#
# No hacer 
## 1. No elimine ninguna parte del codigo fuente para evitar problemas
## 2. No cambiar la version WDK
## 3. No cambiar el controlador de WebViews quitando WebVi y cambiandolo a WDKCONT