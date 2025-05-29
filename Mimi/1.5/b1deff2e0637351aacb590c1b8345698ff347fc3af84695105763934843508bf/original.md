```
connect_param!(m::Model, dst_comp_name::Symbol, dst_par_name::Symbol, 
                src_comp_name::Symbol, src_var_name::Symbol, 
                backup::Union{Nothing, Array}=nothing; ignoreunits::Bool=false, 
                backup_offset::Union{Int, Nothing}=nothing)
```

Bind the parameter `dst_par_name` of one component `dst_comp_name` of model `m` to a variable `src_var_name` in another component `src_comp_name` of the same model using `backup` to provide default values and the `ignoreunits` flag to indicate the need to check match units between the two.  The `backup_offset` argument, which is only valid  when `backup` data has been set, indicates that the backup data should be used for a specified number of timesteps after the source component begins. ie. the value would be  `1` if the destination componentm parameter should only use the source component  data for the second timestep and beyond.
