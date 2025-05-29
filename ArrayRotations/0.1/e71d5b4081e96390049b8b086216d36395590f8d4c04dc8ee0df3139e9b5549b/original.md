```
rotate!(::AuxRotation, A::AbstractVector, tailpos::Integer)
```

Rotates `A` on `tailpos` using at most `n / 2` extra memory, 3n/2 copy-write ops.
