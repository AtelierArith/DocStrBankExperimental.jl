```
shape_nominal_load!(config, data)
```

Shapes the hourly load to match profiles given in `config[:load_shape_file]`.  See [`summarize_table(::Val{:load_shape})`](@ref) for more details

Load power often changes on an hourly basis. The `load_shape_table` allows the user to provide hourly load profiles with which to scale the base load power for load regions, types, or even specific load elements.  Each row of the table represents a set of load elements, and the hourly load profile with which to scale them.  For load elements that fall in multiple sets, the hourly load will be scaled by each profile, in order.
