```
qadic_field(p::Integer, d::Int, var::String = "a"; precision::Int=64, cached::Bool=true, check::Bool=true)
qadic_field(p::ZZRingElem, d::Int, var::String = "a"; precision::Int=64, cached::Bool=true, check::Bool=true)
```

Return an unramified extension $K$ of degree $d$ of a $p$-adic field for the given prime $p$. The generator of $K$ is printed as `var`.

The default absolute precision of elements of $K$ may be set with `precision`.

See also [`unramified_extension`](@ref).
