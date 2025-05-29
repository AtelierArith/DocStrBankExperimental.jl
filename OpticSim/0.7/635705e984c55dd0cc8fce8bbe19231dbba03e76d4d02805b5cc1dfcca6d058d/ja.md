```
BSplineCurve{P,S,N,M} <: Spline{P,S,N,M}
```

`N` は曲線の空間次元です。`M` は曲線の次数、すなわちパラメータ変数 `u` の最高次の幂です。すべての曲線セグメントは同じ次数であると仮定されています。

```julia
BSplineCurve{P,S,N,M}(knots::KnotVector{S}, controlpoints::AbstractArray{MVector{N,S},1})
```
