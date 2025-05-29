```
gridref(p::BNGPoint, n; square=false, sep=' ')
```

Return a string giving an `n`-figure grid reference.  By default, a full reference is given.  If `square` is `true`, then supply the 100 km square name first, then the reference within that square.  The square, eastings and northings are separated by `sep`.

```jldoctest
julia> gridref(BNGPoint(429157, 623009), 8, square=true, sep="_")
"NU_2915_2300"

```
