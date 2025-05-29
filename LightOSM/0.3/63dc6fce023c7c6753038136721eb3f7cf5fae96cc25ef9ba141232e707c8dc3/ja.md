```
heading(a::GeoLocation, b::GeoLocation, return_units::Symbol=:degrees)
heading(a::Node, b::Node, return_units::Symbol=:degrees)
heading(A::Vector{GeoLocation}, B::Vector{GeoLocation}, return_units::Symbol=:degrees)
heading(A::Vector{Node}, B::Vector{Node}, return_units::Symbol=:degrees)
```

2点間の方位（`a`は起点、`b`は目的地）または2つの点のベクトル間の方位を計算します（`A`は起点のベクトル、`B`は目的地のベクトル）。点は`GeoLocation`または`Node`のいずれかです。

選択した`return_units`に応じて、返される角度は`:radians`の場合は[-π, π]の範囲、`:degrees`の場合は[-180, 180]の範囲になります。さらに、aとbの間の直線経路が国際日付変更線を越える場合、目的地の経度を調整します。
