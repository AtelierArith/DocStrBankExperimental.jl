```
update(las::LAS, [attributes]; kws...)
```

Create a copy of a `LAS` that replaces point attributes with the `attributes` provided as a `NamedTuple`. The keyword arguments update the corresponding global attributes of the [`LAS`](@ref).

See also: [`update!`](@ref)
