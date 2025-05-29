```
allocate_variables!(
    vars, modeldata, arrays_idx; 
    [, eltypemap::Dict{String, DataType}],
    [, default_host_dependent_field_data=nothing],
    [, allow_base_link=true],
    [. use_base_transfer_jacobian=true],
    [, use_base_vars=String[]],
    [, check_units_opt=:no])
```

Allocate or link memory for [`VariableDomain`](@ref)s `vars` in `modeldata` array set `arrays_idx`

Element type of allocated Arrays is determined by `eltype(modeldata, arrays_idx)` (the usual case, allowing use of AD types),  which can be overridden by Variable `:datatype` attribute if present (allowing Variables to ignore AD types). `:datatype` may be either a Julia `DataType` (eg Float64), or a string to be looked up in `eltypemap`.

If `allow_base_link==true`, and any of the following are true a link is made to the base array (`arrays_idx=1`),  instead of allocating a new array in array set `arrays_idx`:     - Variable element type matches `modeldata` base eltype (arrays*idx=1)     - `use*base*transfer*jacobian=true`and Variable`:transfer*jacobian`attribute is set     - Variable full name is in`use*base_vars`

Field data type is determined by Variable `:field_data` attribute, optionally this can take a `default_host_dependent_field_data` default for Variables with `host_dependent(v)==true` (these are Variables with no Target or no Property linked, intended to be external dependencies supplied by the solver).

If `check_units_opt != :no` then the `:units` field of linked variable is checked, resulting in either a warning (if `check_units_opt=:warn`) or error (if `check_units_opt=:error`).
