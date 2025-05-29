```
Status(vars)
```

Status type used to store the values of the variables during simulation. It is mainly used as the structure to store the variables in the `TimeStepRow` of a `TimeStepTable` (see  [`PlantMeteo.jl` docs](https://palmstudio.github.io/PlantMeteo.jl/stable/)) of a [`ModelList`](@ref).

Most of the code is taken from MasonProtter/MutableNamedTuples.jl, so `Status` is a MutableNamedTuples with a few modifications, so in essence, it is a stuct that stores a `NamedTuple` of the references to the values of the variables, which makes it mutable.

# Examples

A leaf with one value for all variables will make a status with one time step:

```jldoctest st1
julia> using PlantSimEngine
```

```jldoctest st1
julia> st = PlantSimEngine.Status(Rₛ=13.747, sky_fraction=1.0, d=0.03, aPPFD=1500.0);
```

All these indexing methods are valid:

```jldoctest st1
julia> st[:Rₛ]
13.747
```

```jldoctest st1
julia> st.Rₛ
13.747
```

```jldoctest st1
julia> st[1]
13.747
```

Setting a Status variable is very easy:

```jldoctest st1
julia> st[:Rₛ] = 20.0
20.0
```

```jldoctest st1
julia> st.Rₛ = 21.0
21.0
```

```jldoctest st1
julia> st[1] = 22.0
22.0
```
