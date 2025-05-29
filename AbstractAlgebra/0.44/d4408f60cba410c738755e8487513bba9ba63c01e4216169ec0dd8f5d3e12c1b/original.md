```
mulmod(f::T, g::T, m::T) where T <: RingElem
```

Return `mod(f*g, m)` but possibly computed more efficiently.
