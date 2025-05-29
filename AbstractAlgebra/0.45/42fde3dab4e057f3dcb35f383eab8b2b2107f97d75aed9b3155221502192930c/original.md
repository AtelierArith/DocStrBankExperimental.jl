```
vars(a::FracElem{S}) where {S <: MPolyRingElem{<: RingElement}}
```

Return the variables actually occurring in $a$. Returned variables are elements of `base_ring(a)`. The variables from the numerator go first.
