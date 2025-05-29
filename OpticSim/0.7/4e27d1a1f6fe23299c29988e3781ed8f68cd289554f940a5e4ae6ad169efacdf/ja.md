```
BezierCurve{P,S,N,M} <: Spline{P,S,N,M}
```

`N` は曲線の次元、`M` は曲線の次数です。

```julia
BezierCurve{P,S,N,M}(controlpoints::AbstractArray{<:AbstractArray{S,1},1})
```
