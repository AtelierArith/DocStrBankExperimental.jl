```
divexact_right(f::NCPolyRingElem{T}, g::NCPolyRingElem{T}; check::Bool=true) where T <: NCRingElem
```

Assuming $f = qg$, return $q$. By default if the division is not exact an exception is raised. If `check=false` this test is omitted.
