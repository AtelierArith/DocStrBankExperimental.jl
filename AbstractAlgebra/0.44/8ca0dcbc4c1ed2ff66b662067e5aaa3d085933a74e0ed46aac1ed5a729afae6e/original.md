```
powermod(f::T, e::Int, m::T) where T <: RingElem
```

Return `mod(f^e, m)` but possibly computed more efficiently.
