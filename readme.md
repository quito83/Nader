# Hola Mundo!

### Probando Markdown y recopilando los pasos para crear una dAPP

Creo un directorio/carpeta e instalo **Hardhat** en el. 

```
mkdir hardhat-tutorial
cd hardhat-tutorial
npm init --yes
npm install --save-dev hardhat
```
Uso el comando `npx hardat` para crear un proyecto --> Seleciono Javascript

Installo dependencias:

```
npm install --save-dev @nomicfoundation/hardhat-toolbox
npm install @openzeppelin/contracts
npm install --save @chainlink/contracts
```

En la carpeta contracts creo el contrato extensión `.sol`

Luego instalo .env y creo un archivo en la raiz de hardhat que se llame `.env`

```
npm install dotenv
```
en el archivo `.env` agragar lo siguente: **(la Private key va sin comillas - la HTTP URL va con comillas)**

`
QUICKNODE_HTTP_URL="add-quicknode-http-provider-url-here"

PRIVATE_KEY="add-the-private-key-here"

POLYGONSCAN_KEY="polygonscan-api-key-token-here"
`

Luego cambiamos el `hardhat.config.js`

`
require("@nomicfoundation/hardhat-toolbox");
require("dotenv").config({ path: ".env" });

const QUICKNODE_HTTP_URL = process.env.QUICKNODE_HTTP_URL;
const PRIVATE_KEY = process.env.PRIVATE_KEY;
const POLYGONSCAN_KEY = process.env.POLYGONSCAN_KEY;

module.exports = {
  solidity: "0.8.4",
  networks: {
    mumbai: {
      url: QUICKNODE_HTTP_URL,
      accounts: [PRIVATE_KEY],
    },
  },
  etherscan: {
    apiKey: {
      polygonMumbai: POLYGONSCAN_KEY,
    },
  },
};
`
