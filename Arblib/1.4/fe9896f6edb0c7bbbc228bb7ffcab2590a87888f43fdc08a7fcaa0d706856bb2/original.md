```
getball([T, ] x::ArbOrRef)
```

Returns a tuple `(m::Arf, r::Mag)` where `m` is the midpoint of the ball and `r` is the radius. If `T` is given convert both `m` and `r` to this type, supports `Arf` and `Arb`.

See also [`setball`](@ref) and [`getinterval`](@ref).
