```
set_dimension!(m::Model, name::Symbol, keys::Union{Vector, Tuple, AbstractRange})
```

Set the values of `m` dimension `name` to integers 1 through `count`, if `keys``is an integer; or to the values in the vector or range if`keys`` is either of those types.
