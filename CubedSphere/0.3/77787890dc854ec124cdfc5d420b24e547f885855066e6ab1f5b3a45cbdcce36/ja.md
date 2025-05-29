```
cartesian_to_lat_lon(x, y, z)
```

3Dデカルト座標 `(x, y, z)` を球面上の緯度経度に変換します。度単位のタプル `(latitude, longitude)` を返します。

赤道面は $z = 0$ にあり、緯度は赤道面から測定される角度で、経度は $z$-軸の周りで $x$-軸 ($y = 0$) から反時計回り（東向き）に測定されます。

# 例

北極の緯度経度を求める

```jldoctest 1
julia> using CubedSphere

julia> x, y, z = (0, 0, 6.4e6); # 北極のデカルト座標 [メートル単位]

julia> cartesian_to_lat_lon(x, y, z)
(90.0, 0.0)
```

単位球上のいくつかの点について、期待される答えが得られることを確認しましょう。

```jldoctest 1
julia> cartesian_to_lat_lon(√2/4, -√2/4, √3/2)
(59.99999999999999, -45.0)

julia> cartesian_to_lat_lon(-√6/4, √2/4, -√2/2)
(-45.00000000000001, 150.0)
```
