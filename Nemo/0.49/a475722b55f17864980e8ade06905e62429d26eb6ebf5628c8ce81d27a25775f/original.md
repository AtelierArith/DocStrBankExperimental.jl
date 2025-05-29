```
unramified_extension(Qp::PadicField, d::Int, var::String = "a"; precision::Int=64, cached::Bool=true)
```

Return an unramified extension $K$ of degree $d$ of the given $p$-adic field `Qp`. The generator of $K$ is printed as `var`.

The default absolute precision of elements of $K$ may be set with `precision`.
