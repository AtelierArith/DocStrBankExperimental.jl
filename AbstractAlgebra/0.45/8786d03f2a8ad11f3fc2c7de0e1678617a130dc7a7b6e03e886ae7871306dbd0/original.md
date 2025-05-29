```
Base.sqrt(f::PolyRingElem{T}; check::Bool=true) where T <: RingElement
```

Return the square root of $f$. By default the function checks the input is square and raises an exception if not. If `check=false` this check is omitted.
