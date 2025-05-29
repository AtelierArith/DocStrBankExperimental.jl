```
check_data_type(existing_values, data_type::Union{Missing, Type})
```

Helper function for [`check_values`](@ref) implementations: check `existing_values` are consistent with `data_type` (if supplied), throw exception if not.
