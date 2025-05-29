```julia
launch(comp)

```

Returns a tuple of tasks so that `trigger` link and `output` bus of `comp` is drivable. When launched, `comp` is ready to be driven from its `trigger` link. See also: [`drive!(comp::AbstractComponent, t)`](@ref)
