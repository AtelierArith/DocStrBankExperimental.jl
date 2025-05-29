```
f16(m)
```

Converts the `eltype` of `m` *floating point* values to `Float16`. To avoid recursion into structs mark them with `Functors.@leaf`.
