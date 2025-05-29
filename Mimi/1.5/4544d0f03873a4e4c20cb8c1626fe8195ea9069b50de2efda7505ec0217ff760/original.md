```
set_dimension!(ccd::CompositeComponentDef, name::Symbol, keys::Union{Int, Vector, Tuple, AbstractRange})
```

Set the values of `ccd` dimension `name` to integers 1 through `count`, if `keys` is an integer; or to the values in the vector or range if `keys` is either of those types.
