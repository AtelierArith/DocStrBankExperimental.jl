Call all SPICE Utilities from within Julia!

!!! warning
    This package is not affiliated with or endorsed by NASA, JPL, Caltech, or any other organization! This is an independently written package by an astrodynamics hobbyist.


# Extended help

## README

[![Tests](https://github.com/cadojo/SPICEApplications.jl/workflows/UnitTests/badge.svg)](https://github.com/cadojo/SPICEApplications.jl/actions?query=workflow%3AUnitTests) [![Docs](https://github.com/cadojo/SPICEApplications.jl/workflows/Documentation/badge.svg)](https://cadojo.github.io/SPICEApplications.jl) [![SciML Code Style](https://img.shields.io/static/v1?label=Style&message=SciML&color=9668e2&labelColor=3E474F)](https://github.com/SciML/SciMLStyle)

# `SPICEApplications`

*Generate ephemeris kernel files using NASA JPL's `SPICEApplications` program, all from within Julia!*

**Please consider all minor changes breaking until `v1.0`!**

> **Warning**
>
> This package is not affiliated with or endorsed by NASA, JPL, Caltech, or any other organization! This is an independently written package by an astrodynamics hobbyist.


## Installation

Choose one of the following two lines!

```julia
import Pkg; Pkg.add("SPICEApplications");
```

```julia
]add SPICEApplications # in Julia's REPL
```

## Credits

NASA JPL developed and maintains the [NAIF SPICE Toolkit](https://naif.jpl.nasa.gov/naif/toolkit.html), including `SPICEApplications`. Helge Eichhorn developed and maintains [`SPICE.jl`](https://github.com/JuliaAstro/SPICE.jl), as well as the [Julia wrappers](https://juliahub.com/ui/Packages/CSPICE_jll/XJqVo/67.0.0+0) around the SPICE Toolkit.

## License

MIT License

Copyright (c) 2023 Joe Carpinelli

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Exports

  * [`brief`](@ref)
  * [`chronos`](@ref)
  * [`ckbrief`](@ref)
  * [`commnt`](@ref)
  * [`dskbrief`](@ref)
  * [`dskexp`](@ref)
  * [`frmdiff`](@ref)
  * [`inspekt`](@ref)
  * [`mkdsk`](@ref)
  * [`mkspk`](@ref)
  * [`msopck`](@ref)
  * [`spacit`](@ref)
  * [`spkdiff`](@ref)
  * [`spkmerge`](@ref)
  * [`tobin`](@ref)
  * [`toxfr`](@ref)

## Imports

  * `Base`
  * `Core`
  * `DocStringExtensions`
