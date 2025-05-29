```julia
save_rocket(rocket::Rocketeer.RocketModule)
save_rocket(
    rocket::Rocketeer.RocketModule,
    filepath::AbstractString
)

```

# Summary

Save the [`RocketModule`](@ref) parameters to a `.jld2` file.

# Arguments

  * `rocket::RocketModule`: the [`RocketModule`](@ref) to save.
  * `filepath::AbstractString`: default `rocket.jld2`, path to `.jld2` for saving rocket parameters.

# Method List / Definition Locations

```julia
save_rocket(rocket)
save_rocket(rocket, filepath)
```

defined at [`packages/Rocketeer/tbPiD/src/lib/rocket.jl:196`](file:///home/terasaki/.julia/packages/Rocketeer/tbPiD/src/lib/rocket.jl).
