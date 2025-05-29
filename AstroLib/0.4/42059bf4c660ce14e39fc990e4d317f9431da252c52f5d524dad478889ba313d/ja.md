```
geodetic2geo(latitude, longitude, altitude) -> latitude, longitude, altitude
geodetic2geo(latitude, longitude, altitude, planet) -> latitude, longitude, altitude
geodetic2geo(latitude, longitude, altitude, equatorial_radius, polar_radius) -> latitude, longitude, altitude
```

### 目的

測地線（または惑星測地線）から地理座標への変換。

### 説明

測地線（緯度、経度、高度）から地理（緯度、経度、高度）への変換を行います。地理座標では、地球は赤道半径と等しい半径の完璧な球体と仮定されます。測地線（または楕円体）座標系は、地球の扁平率を考慮に入れています。

地理的および測地的経度は同一です。測地的緯度は、局所的な天頂と赤道面との間の角度です。地理的および測地的高度は、衛星と地面との間の最も近い距離です。

### 引数

この関数には2つの基本メソッドがあります。すべてのメソッドに共通で常に必須の引数は `latitude`、`longitude`、および `altitude` です：

  * `latitude`: 測地的緯度（度単位）。
  * `longitude`: 測地的経度（度単位）。
  * `altitude`: 測地的高度（キロメートル単位）。

地理座標に変換するには、惑星の赤道半径と極半径をカスタムで提供するか、太陽系の惑星のいずれかの値を使用することができます（冥王星を含む）。

赤道半径と極半径を明示的に指定するメソッドを使用したい場合、追加の必須引数は次のとおりです：

  * `equatorial_radius`: 物体の赤道半径の値（キロメートル単位）。
  * `polar_radius`: 物体の極半径の値（キロメートル単位）。

代わりに、惑星の選択を使用したい場合、唯一の追加引数は惑星名です：

  * `planet`（オプションの文字列引数）：太陽系の惑星の名前を含む文字列（「水星」から「冥王星」まで）。省略した場合（つまり、`latitude`、`longitude`、および `altitude` のみが提供される場合）、デフォルトは「地球」です。

すべての場合において、3つの座標は3タプル `(latitude, longitude, altitude)` として渡すことができます。さらに、測地的 `latitude`、`longitude`、および `altitude` は同じ長さの配列として与えることができます。

### 出力

指定された赤道半径と極半径を持つ物体の地理座標における3タプル `(latitude, longitude, altitude)`（デフォルトは地球）。

測地座標が配列として与えられた場合、同じ長さの配列の3タプルが返されます。

### 方法

Stephen P. Keeler と Yves Nievergelt, "Computing geodetic coordinates", SIAM Rev. Vol. 40, No. 2, pp. 300-309, June 1998 (DOI:[10.1137/S0036144597323921](http://dx.doi.org/10.1137/S0036144597323921))。

惑星定数は "Allen's Astrophysical Quantities", Fourth Ed., (2000) からのものです。

### 例

地球の測地的北極（緯度: 90°, 経度: 0°, 高度 0 km）の地理座標を求めます：

```jldoctest
julia> using AstroLib

julia> geodetic2geo(90, 0, 0)
(90.0, 0.0, -21.38499999999931)
```

同様に木星の場合：

```jldoctest
julia> using AstroLib

julia> geodetic2geo(90, 0, 0, "Jupiter")
(90.0, 0.0, -4638.0)
```

赤道半径 8724.32 km および極半径 8619.19 km の惑星上の測地座標（緯度、経度、高度）= (43.16°, -24.32°, 3.87 km) の地理座標を求めます：

```jldoctest
julia> using AstroLib

julia> geodetic2geo(43.16, -24.32, 3.87, 8724.32, 8619.19)
(42.46772711708433, -24.32, -44.52902080669082)
```

### 注意

`geo2geodetic` は地理（または惑星地理）から測地座標への変換を行います。

この関数のコードは IDL Astronomy User's Library に基づいています。 ```
