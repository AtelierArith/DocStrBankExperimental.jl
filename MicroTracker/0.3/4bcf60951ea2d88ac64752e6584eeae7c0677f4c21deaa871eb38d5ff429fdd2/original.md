```
link(particle_data::AbstractDataFrame, linking_settings::NamedTuple; trackpykwargs...)
```

Use trackpy to link particle data into trajectories across frames.

See the [Linking Settings](@ref) docs for the fields and format of `linking_settings`. Any kwargs will be passed to the trackpy.link function [trackpy.link](https://soft-matter.github.io/trackpy/v0.6.1/generated/trackpy.link.html#trackpy.link).

# Example

```julia-repl
julia> link(particle_data, linking_settings)
```
