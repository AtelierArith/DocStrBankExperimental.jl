```
dot(a::MultiValue{Tuple{...,D}}, b::MultiValue{Tuple{D,...}})
a ⋅¹ b
a ⋅ b
```

Inner product of two tensors `a` and `b`, that is the single contraction of the last index of `a` with the first index of `b`. The corresponding dimensions `D` must match. No symmetry is preserved.
