```
distance(A::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}},
         B::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}},
         type::Symbol=:haversine
         )
```

2つの点または2つの点のベクトル間の距離（km）を計算します。

# 引数

  * `A::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}}`: 原点の点のベクトル。
  * `B::Union{Vector{GeoLocation}, GeoLocation, Vector{<:Node}, Node, Vector{<:AbstractFloat}}`: 目的地の点のベクトル。
  * `method::Symbol=:haversine`: `:haversine` または `:euclidean` のいずれか。

# 戻り値

  * 原点と目的地の点間の距離（km）。
