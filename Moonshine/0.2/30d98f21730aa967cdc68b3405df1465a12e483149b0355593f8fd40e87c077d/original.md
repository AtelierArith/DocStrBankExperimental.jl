```
latitudes(genealogy[, vs])
```

Return the latitudes of (a subset of) the internal vertices of a genealogy.

See also [`latitude`](@ref) to get the latitude of a single vertex.

# Implementation

A default implementation for `latitudes(::AbstractGenealogy, ::Any)` is available; only `latitudes(::T)` is required.

# Methods

```julia
latitudes(genealogy, vs)
```

defined at [`packages/Moonshine/7JVTP/src/Genealogy.jl:80`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl).

```julia
latitudes(arg)
latitudes(tree)
```

defined at [`packages/Moonshine/7JVTP/src/genealogy_common.jl:31`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/genealogy_common.jl).
