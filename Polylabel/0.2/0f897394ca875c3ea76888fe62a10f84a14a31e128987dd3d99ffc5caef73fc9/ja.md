```
polylabel(polygon::Polygon; rtol::Real = 0.01, atol::Union{Nothing, Real} = nothing)::Tuple{Float64, Float64}
polylabel(multipoly::MultiPolygon; rtol::Real = 0.01, atol::Union{Nothing, Real} = nothing)::Tuple{Float64, Float64}
```

`polylabel`は、指定されたポリゴンまたはマルチポリゴンのアクセス不可能点を見つけ、その座標を2タプルの`(x, y)`として返します。許容誤差を指定することができます。

`GeoInterface.jl`のポリゴンまたはマルチポリゴンの特性を表現する任意のジオメトリをこのメソッドに渡すことができますが、ポリゴンの`coordinates`、`getexterior`、および`gethole`インターフェースに加えて、`GeoInterface`メソッド`extent`、`contains`、および`centroid`を実装している必要があります。

`rtol`は相対許容誤差、`atol`は絶対許容誤差です（`Base.isapprox`と同様の意味で）。`atol`が提供されると、`rtol`は上書きされます。

!!! warning
    この関数のパフォーマンスはまだ積極的に改善中です。特に符号付き距離関数には最適化が必要です。それまでは、Python/JSの同等のものよりもはるかに遅くなります。

