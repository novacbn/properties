# properties

> **gmodproj >= 0.4.0**

## Requirements

* [moonscript](https://github.com/leafo/moonscript) - Via `require` for MoonScript-based property files.
* [lpeg](http://www.inf.puc-rio.br/~roberto/lpeg) (or a suitable polyfill such as [LuLPeg](https://github.com/pygy/LuLPeg)) - Required for MoonScript-based property files.

## Description

A standalone platform-independent Lua library, facilitating encoding and decoding of Lua tables into human-readable properties files.

## Documentation

Currently missing a more readable form of documentation, although everything under the `src` directory annotated.

## Properties Format

Currently `properities` only supports two encoding formats usable in `encode(table value, table options?)` and `decode(string value, table options?)`.

### EncoderOptions.encoderType == `lua`

Supports encoding and decoding of Lua tables into human-readable Lua files

**sample.lprop**
```lua
tableProp = {
    testProp = 'testValue'
}
```

**main.lua**
```lua
local properties    = import 'novacbn/properties'
local tableProp     = properties.decode(..., {
    encoderType = 'lua'
})

print(tableProp.testProp) -- prints 'testValue'
```

### EncoderOptions.encoderType == `moonscript`

Supports encoding and decoding of Lua tables into human-readable [MoonScript](https://moonscript.org) files.

**sample.mprop**
```moonscript
tableProp:
    testProp: 'testValue'
```

**main.lua**
```lua
local properties    = import 'novacbn/properties'
local tableProp     = properties.decode(..., {
    encoderType = 'lua'
})

print(tableProp.testProp) -- prints 'testValue'
```

## Installation

If wanting to use with a standard Lua platform, download the latest `properties.lua` build from [Releases](https://github.com/novacbn/properties/releases). And use it as you would any other library.

Alternatively, if using with `gmodproj`. Download the latest `.zip` or `.tar.gz` archive from the [Releases](https://github.com/novacbn/properties/releases). Extract the contents of `src` directory into your project's `packages` directory under a `novacbn/properties` directory.

## Building

```bash
# Clone the repository
git clone https://github.com/novacbn/properties

# Move into the project and make the build directory
cd properties
mkdir ./dist

# Building the project will produce `./dist/properties.lua`
gmodproj build # Or gmodproj build production
```