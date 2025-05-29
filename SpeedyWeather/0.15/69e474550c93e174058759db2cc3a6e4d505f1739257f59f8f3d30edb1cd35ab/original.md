```julia
tree(
    S::SpeedyWeather.Simulation{M};
    modules,
    with_size,
    kwargs...
)

```

Create a tree of fields inside a Simulation instance and fields within these fields as long as they are defined within the modules argument (default SpeedyWeather). Other keyword arguments are `max_level::Integer=10`, `with_types::Bool=false` or `with_size::Bool=false`.
