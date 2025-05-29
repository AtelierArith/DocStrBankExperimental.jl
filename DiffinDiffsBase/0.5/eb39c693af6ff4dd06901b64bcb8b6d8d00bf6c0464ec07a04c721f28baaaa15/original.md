```
diff(panel::PanelStructure, v::AbstractArray; kwargs...)
```

Return the differences of `v` within observations for each unit in `panel`. By default, it calculates the first differences. See also [`diff!`](@ref).

# Keywords

  * `order::Integer=1`: the order of differences to be taken.
  * `l::Integer=1`: the time interval between each pair of observations.
  * `default=missing`: default values for indices where the differences do not exist.
