```
p ⋅ q
```

Evaluate the inner ("dot") product between two quaternions.  Equal to the scalar part of `p * conj(q)`.

Note that this function is not very commonly used, except as a quick way to determine whether the two quaternions are more anti-parallel than parallel, for functions like [`unflip`](@ref).
