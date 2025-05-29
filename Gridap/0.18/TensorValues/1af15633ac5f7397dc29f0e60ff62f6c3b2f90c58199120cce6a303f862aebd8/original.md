```
inner(a::MultiValue{S}, b::MultiValue{S}) -> scalar
a ⊙ b
```

Inner product of two tensors, that is the full contraction along each indices. The size `S` of `a` and `b` must match.
