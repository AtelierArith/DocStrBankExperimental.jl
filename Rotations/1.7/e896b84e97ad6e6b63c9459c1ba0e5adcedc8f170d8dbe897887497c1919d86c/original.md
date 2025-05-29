```
(*)(q::QuatRotation, w::QuatRotation)
```

Quternion Composition

Equivalent to

```julia
lmult(q) * SVector(w)
rmult(w) * SVector(q)
```

Sets the output mapping equal to the mapping of `w`
