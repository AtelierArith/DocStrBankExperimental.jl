```
connect_param!(m::Model, dst::Pair{Symbol, Symbol}, src::Pair{Symbol, Symbol}, backup::Array; ignoreunits::Bool=false)
```

Bind the parameter `dst[2]` of one component `dst[1]` of model `m` to a variable `src[2]` in another component `src[1]` of the same model using `backup` to provide default values and the `ignoreunits` flag to indicate the need to check match units between the two.  The `backup_offset` argument, which is only valid  when `backup` data has been set, indicates that the backup data should be used for a specified number of timesteps after the source component begins. ie. the value would be  `1` if the destination componentm parameter should only use the source component  data for the second timestep and beyond.
