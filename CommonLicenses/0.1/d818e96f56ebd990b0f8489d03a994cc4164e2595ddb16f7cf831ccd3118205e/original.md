Display open-source software (and other) licenses inline in your executable documents!

# Extended help

## README

[![Tests](https://github.com/cadojo/CommonLicenses.jl/workflows/UnitTests/badge.svg)](https://github.com/cadojo/CommonLicenses.jl/actions?query=workflow%3AUnitTests) [![Docs](https://github.com/cadojo/CommonLicenses.jl/workflows/Documentation/badge.svg)](https://cadojo.github.io/CommonLicenses.jl/dev)

# `CommonLicenses.jl`

*Executable licenses for executable documents!*

## Installation

*Choose one of the lines below!*

```julia
import Pkg; Pkg.add("CommonLicenses")
```

```julia
# In a Julia REPL
]add CommonLicenses
```

## Motivation

*Why does this exist?*

Imagine you're writing a blog post. Or a [Pluto](https://plutojl.org) notebook. Or a [Jupyter](https://jupyter.org) notebook. Or whatever! You're writing words alongside content, and you'd like to license your work. The license needs to stand *alone* with your document; the "naive" solution is to find the contents of your standard license file, and paste the license into a block of text somewhere in your document. Cool. Two weeks later you're writing *another* blog post, or whatever. You need to re-find the contents of this license. Not a big deal, but this gets a bit cumbersome, right?

Enter: `CommonLicenses.jl`. This package provides every standard license tracked by the [SPDX License List](https://spdx.org/licenses/), so all you need to do is install this package, and print your desired license wherever you want it!

## Usage

*Try it out for yourself!*

```julia
julia> using CommonLicenses

julia> using CommonLicenses: MIT, Unlicense

julia> MIT()

julia> Unlicense()

julia> CommonLicenses.text(MIT(copyright="Joe(y)"))

julia> CommonLicenses.name(License("CC-BY-4.0"))
```

## Credits

*Built on top of lots of helpful projects!*

This package was developed independently of [`PkgLicenses.jl`](https://github.com/JuliaPackaging/PkgLicenses.jl/tree/master), though it does look like `JuliaPackaging` got there first! This package adds goodies on top of the functionality of `PkgLicenses.jl`, including `MIME` type support, and licenses for non-software projects such as Creative Commons.

The [SPDX License List](https://spdx.org/licenses/) is used to fetch the contents for each requested license. The GitHub [License API](https://docs.github.com/en/rest/licenses) is used to find additional metadata for each license, if available.

## License

MIT License

Copyright (c) 2023 Joe Carpinelli

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Exports

  * [`License`](@ref)

## Imports

  * `Base`
  * `Core`
  * `Dates`
  * `DocStringExtensions`
  * `HTTP`
  * `JSON`
  * `Scratch`
