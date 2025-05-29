```julia
load_rocket() -> Any
load_rocket(filepath::AbstractString) -> Any

```

# Summary

Load and return a [`RocketModule`](@ref) with existing parameters from a `.jld2` file.

# Arguments

  * `filepath::AbstractString`: default `rocket.jld2`, path to the `.jld2` containing rocket parameters.

# Method List / Definition Locations

```julia
load_rocket()
load_rocket(filepath)
```

defined at [`packages/Rocketeer/tbPiD/src/lib/rocket.jl:210`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl).
