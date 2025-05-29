```
Spline(y::Array{T,1}, kind::Symbol = :open)::Spline where {T<:Number}
```

`Spline(vals,kind)` returns a cubic spline based on the values in `vals`. The resulting spline `S` will have the property that `S(1)==y[1]`, `S(2)==y[2]`, and so on up to `S(n)==y[n]` where `n` is the length of `y`.

  * If `kind` is `:open` then the second derivatives at the end points will be zero. (This is the default.)
  * If `kind` is `:closed` then we assume that we are interpolating a periodic function where `S(n+1)==S(1)`.
