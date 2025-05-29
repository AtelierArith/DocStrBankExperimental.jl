```
divexact_left(a::NCPolyRingElem, b::Union{Integer, Rational, AbstractFloat}; check::Bool=true)
```

Assuming $a = bq$, return $q$. By default if the division is not exact an exception is raised. If `check=false` this test is omitted.
