```
f32(m)
```

Converts the `eltype` of `m` *floating point* values to `Float32`. To avoid recursion into structs mark them with `Functors.@leaf`.
