```
GeodesicBetween(DM::DataModel, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
GeodesicBetween(Metric::Function, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
```

与えられた2点間の測地線をパラメータ多様体上で計算し、計量の式を提供します。

キーワード `BVPmeth` を使用して、`BoundaryValueDiffEq.jl` パッケージからBVP積分アルゴリズムを渡します。キーワード `approx=true` を設定することで、クリストッフェル記号は定数であると仮定され、初期位置で一度だけ計算されます。これにより計算が大幅に簡素化されますが、リッチ曲率の大きさによっては不正確な近似となる可能性もあります。
