```
keyedreduce(op, key::AbstractVector{T}, a, init=0.0) where T
```

Similar to `countmap` returning a dictionary mapping unique key in `key` to the  reduction the given collection itr with the given binary operator `op`.

```
julia> keyedreduce(+, [:a, :b, :a], [7, 3, 2])
Dict{Symbol, Float64} with 2 entries:
  :a => 9.0
  :b => 3.0
```
