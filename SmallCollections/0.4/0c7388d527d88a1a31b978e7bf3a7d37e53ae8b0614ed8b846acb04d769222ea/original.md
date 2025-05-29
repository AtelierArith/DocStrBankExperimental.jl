```
prepend(v::V, ws...) where V <: AbstractCapacityVector -> V
```

Prepend all elements of the collections `ws` to `v` and return the new vector. Note that the resulting `AbstractCapacityVector` has the same capacity as `v`.

See also `Base.prepend!`.
