```
deleteat(v::V, i::Integer) where V <: AbstractCapacityVector -> V
```

Return the `AbstractCapacityVector` obtained from `v` by deleting the element at position `i`. The latter must be between `1` and `length(v)`.

See also `Base.deleteat!`, `BangBang.deleteat!!`.
