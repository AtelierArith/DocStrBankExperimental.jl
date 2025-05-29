```
update!(las::LAS, [attributes]; kws...)
```

Update a `LAS` by replacing point attributes with the `attributes` provided as a `NamedTuple`. This is only supported if the point records of the `LAS` have been loaded into memory.

The keyword arguments update the corresponding global attributes of the [`LAS`](@ref), of which only `coord_min`, `coord_max`, and `return_counts` can be modified in-place.

See also: [`update`](@ref)
