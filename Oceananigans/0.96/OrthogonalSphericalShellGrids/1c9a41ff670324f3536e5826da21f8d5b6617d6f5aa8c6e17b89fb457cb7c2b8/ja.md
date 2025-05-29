```
TripolarGrid(arch = CPU(), FT::DataType = Float64;
             size,
             southernmost_latitude = -80,
             halo = (4, 4, 4),
             radius = R_Earth,
             z = (0, 1),
             north_poles_latitude = 55,
             first_pole_longitude = 70)
```

球面上の `OrthogonalSphericalShellGrid` 三極グリッドを返します。三極グリッドは、北極の特異点を、90ᵒ未満の `north_poles_latitude` にある他の2つの特異点で置き換えます。

# 位置引数

  * `arch`: グリッドに使用するアーキテクチャ。デフォルトは `CPU()`。
  * `FT::DataType`: グリッドに使用するデータ型。デフォルトは `Float64`。

# キーワード引数

  * `size`: （経度、緯度、垂直）次元のセルの数。
  * `southernmost_latitude`: グリッドの最南端の `Center` 緯度。デフォルトは -80。
  * `halo`: （経度、緯度、垂直）次元のハローサイズ。デフォルトは (4, 4, 4)。
  * `radius`: 球殻の半径。デフォルトは `R_Earth`。
  * `z`: グリッドの垂直 $z$-座標範囲。デフォルトは (0, 1)。
  * `first_pole_longitude`: 最初の「北」特異点の経度。第二の特異点は `first_pole_longitude + 180ᵒ` に位置します。
  * `north_poles_latitude`: 「北」特異点の緯度。

!!! warning "経度座標は偶数のセル数でなければなりません"
    `size` は、経度、緯度、垂直方向のグリッドサイズの3タプルです。領域の北端での折りたたみの要件により、グリッドの経度サイズ（すなわち、`size` の最初の要素）は *偶数* でなければなりません！


!!! info "北極の特異点"
    北の特異点は次の位置にあります: `i = 1`, `j = Nφ` および `i = Nλ ÷ 2 + 1`, `j = Nφ`。

