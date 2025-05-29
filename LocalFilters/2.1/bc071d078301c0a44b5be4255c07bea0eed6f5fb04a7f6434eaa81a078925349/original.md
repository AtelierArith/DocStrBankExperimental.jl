```
localmean!(dst, A, B=3; null=zero(eltype(dst)), order=FORWARD_FILTER) -> dst
```

overwrites `dst` with the local mean of `A` in a neighborhood defined by `B` and returns `dst`.

Keyword `null` may be used to specify the value of the result where the sum of the weights in the a neighborhood is zero.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

See also [`localmean`](@ref) and [`localfilter!`](@ref).
