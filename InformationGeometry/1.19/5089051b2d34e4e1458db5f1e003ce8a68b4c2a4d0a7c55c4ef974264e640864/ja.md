```
GeodesicDistance(DM::DataModel, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
GeodesicDistance(Metric::Function, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-10)
```

点 `P` と `Q` を結ぶ測地線の長さを計算します。
