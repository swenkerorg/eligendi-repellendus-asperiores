# @swenkerorg/eligendi-repellendus-asperiores
[![NPM version](https://img.shields.io/npm/v/@swenkerorg/eligendi-repellendus-asperiores.svg)](http://npmjs.com/package/@swenkerorg/eligendi-repellendus-asperiores)
[![Build Status](https://github.com/swenkerorg/eligendi-repellendus-asperiores/workflows/CI/badge.svg)](https://github.com/swenkerorg/eligendi-repellendus-asperiores/actions?query=workflow%3A%22CI%22)
[![Discord](https://img.shields.io/badge/chat-on%20discord-brightgreen.svg)](https://discord.gg/GsEFRM8)
[![Try it on gitpod](https://img.shields.io/badge/try-on%20gitpod-brightgreen.svg)](https://gitpod.io/#https://github.com/swenkerorg/eligendi-repellendus-asperiores)


Basic argument parsing library using yargs-parser with built-in help screen

## Installation

`npm install @swenkerorg/eligendi-repellendus-asperiores`

## Usage

See index.d.ts for API

#### CommonJS import

```js
const args = require('@swenkerorg/eligendi-repellendus-asperiores')({
  name: '@swenkerorg/eligendi-repellendus-asperiores-example',
  version: '1.0.0',
  description: 'A basic example of @swenkerorg/eligendi-repellendus-asperiores',
  errorOnUnknown: true,
  options: {
    version: { type: String, description: 'Version to connect as', alias: 'v' },
    port: { type: Number, description: 'Port to listen on', default: 25565 },
    online: { type: Boolean, description: 'Whether to run in online mode' },
    path: { type: String, description: 'Path to the server directory', default: '.' }
  }
})

console.log(args)
```

After being ran with `node index.js --version 1.16` (or using `-v 1.16` alias) we would get:

```js
{ version: '1.16.1', port: 25565, online: false, path: '.' }
```

Please note Boolean options do not need arguments, simply passing them as an argument will resolve
them to be true. If you want to force an argument, set type to a String to handle yourself.

Extraneous arguments (when not using errorOnExtra) are stored in the `_` index of the output. The nested `_` contains positionals.

### Help screen
If we run with --help or get a argument error, we see the help screen:

```
> node example.js --help   
@swenkerorg/eligendi-repellendus-asperiores-example - v1.0.0
A basic example of @swenkerorg/eligendi-repellendus-asperiores

Options:
  --version     Version to connect as
  --port        Port to listen on  (default: 25565)
  --online      Whether to run in online mode
  --path        Path to the server directory  (default: .)
```

### Custom args
The second argument is the custom arg array if any, if it's not set, we default to `process.argv`.

```js
require('@swenkerorg/eligendi-repellendus-asperiores')(options, process.argv)
```

### ES6 import
```js
import basicArg from '@swenkerorg/eligendi-repellendus-asperiores'
const args = basicArg({
  name: '@swenkerorg/eligendi-repellendus-asperiores-example',
  version: '1.0.0',
  description: 'A basic example of @swenkerorg/eligendi-repellendus-asperiores',
  throwOnError: false, // Throw an error instead of calling process.exit() with help screen (default: false)
  helpCommand: 'help', // The -- command for opening the built-in help screen (default: help)
  options: {
    version: { type: String, description: 'Version to connect as', alias: 'v' },
    port: { type: Number, description: 'Port to listen on', default: 25565 },
    online: { type: Boolean, description: 'Whether to run in online mode' },
    path: { type: String, description: 'Path to the server directory', default: '.' }
  },
  // validate (args) { return true } /* optional fn to verify the args before returning them; non-true return value will print help screen */
})
// ...
```

## Testing

```npm test```

## History

See [history](HISTORY.md)
