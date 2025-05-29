```
divexact_right(a::NCPolyRingElem{T}, b::T; check::Bool=true) where T <: NCRingElem
```

Assuming $a = qb$, return $q$. By default if the division is not exact an exception is raised. If `check=false` this test is omitted.
