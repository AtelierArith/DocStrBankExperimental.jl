```
rotate!(::RevRotation, A::AbstractVector, tailpos::Integer)
```

Rotates `A` on `tailpos` using $O(1)$ extra memory, yet using several 2n copy-write ops (triple reversing)
