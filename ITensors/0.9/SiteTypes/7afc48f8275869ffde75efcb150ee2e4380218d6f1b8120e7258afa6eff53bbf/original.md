SiteType is a parameterized type which allows making Index tags into Julia types. Use cases include overloading functions such as `op`, `siteinds`, and `state` which generate custom operators, Index arrays, and IndexVals associated with Index objects having a certain tag.

To make a SiteType type, you can use the string macro notation: `SiteType"MyTag"`

To make a SiteType value or object, you can use the notation: `SiteType("MyTag")`

There are currently a few built-in site types recognized by `jl`. The system is easily extensible by users. To add new operators to an existing site type, or to create new site types, you can follow the instructions [here](https://docs.itensor.org/ITensorMPS/stable/examples/Physics.html).

The current built-in site types are:

  * `SiteType"S=1/2"` (or `SiteType"S=½"`)
  * `SiteType"S=1"`
  * `SiteType"Qubit"`
  * `SiteType"Qudit"`
  * `SiteType"Boson"`
  * `SiteType"Fermion"`
  * `SiteType"tJ"`
  * `SiteType"Electron"`

# Examples

Tags on indices get turned into SiteTypes internally, and then we search for overloads of functions like `op` and `siteind`. For example:

```julia
julia> s = siteind("S=1/2")
(dim=2|id=862|"S=1/2,Site")

julia> @show op("Sz", s);
op(s, "Sz") = ITensor ord=2
Dim 1: (dim=2|id=862|"S=1/2,Site")'
Dim 2: (dim=2|id=862|"S=1/2,Site")
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 0.5   0.0
 0.0  -0.5

julia> @show op("Sx", s);
op(s, "Sx") = ITensor ord=2
Dim 1: (dim=2|id=862|"S=1/2,Site")'
Dim 2: (dim=2|id=862|"S=1/2,Site")
NDTensors.Dense{Float64,Array{Float64,1}}
 2×2
 0.0  0.5
 0.5  0.0

julia> @show op("Sy", s);
op(s, "Sy") = ITensor ord=2
Dim 1: (dim=2|id=862|"S=1/2,Site")'
Dim 2: (dim=2|id=862|"S=1/2,Site")
NDTensors.Dense{Complex{Float64},Array{Complex{Float64},1}}
 2×2
 0.0 + 0.0im  -0.0 - 0.5im
 0.0 + 0.5im   0.0 + 0.0im

julia> s = siteind("Electron")
(dim=4|id=734|"Electron,Site")

julia> @show op("Nup", s);
op(s, "Nup") = ITensor ord=2
Dim 1: (dim=4|id=734|"Electron,Site")'
Dim 2: (dim=4|id=734|"Electron,Site")
NDTensors.Dense{Float64,Array{Float64,1}}
 4×4
 0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  1.0
```

Many operators are available, for example:

  * `SiteType"S=1/2"`: `"Sz"`, `"Sx"`, `"Sy"`, `"S+"`, `"S-"`, ...
  * `SiteType"Electron"`: `"Nup"`, `"Ndn"`, `"Nupdn"`, `"Ntot"`, `"Cup"`,  `"Cdagup"`, `"Cdn"`, `"Cdagdn"`, `"Sz"`, `"Sx"`, `"Sy"`, `"S+"`, `"S-"`, ...
  * ...

You can view the internal SiteType definitions and operators [here](https://docs.itensor.org/ITensorMPS/stable/IncludedSiteTypes.html).
