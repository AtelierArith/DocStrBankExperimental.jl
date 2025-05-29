```
padic_field(p::Integer; precision::Int=64, cached::Bool=true, check::Bool=true)
padic_field(p::ZZRingElem; precision::Int=64, cached::Bool=true, check::Bool=true)
```

Return the $p$-adic field for the given prime $p$. The default absolute precision of elements of the field may be set with `precision`.
