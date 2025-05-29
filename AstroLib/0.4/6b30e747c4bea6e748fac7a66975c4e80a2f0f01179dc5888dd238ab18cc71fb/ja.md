```
geo2geodetic(latitude, longitude, altitude) -> latitude, longitude, altitude
geo2geodetic(latitude, longitude, altitude, planet) -> latitude, longitude, altitude
geo2geodetic(latitude, longitude, altitude, equatorial_radius, polar_radius) -> latitude, longitude, altitude
```

### 目的

地理座標（または惑星座標）から測地座標に変換します。

### 説明

地理座標（緯度、経度、高度）から測地座標（緯度、経度、高度）に変換します。地理座標では、地球は赤道半径と等しい半径の完璧な球体と仮定されます。測地座標（または楕円体座標）系は、地球の扁平率を考慮に入れています。

地理的および測地的経度は同一です。測地的緯度は、局所的な天頂と赤道面との間の角度です。地理的および測地的高度は、衛星と地面との間の最も近い距離です。

### 引数

この関数には2つの基本メソッドがあります。すべてのメソッドに共通で常に必須の引数は `latitude`、`longitude`、および `altitude` です：

  * `latitude`: 地理的緯度（度単位）。
  * `longitude`: 地理的経度（度単位）。
  * `altitude`: 地理的高度（キロメートル単位）。

測地座標に変換するには、惑星の赤道半径と極半径をカスタムで提供するか、太陽系の惑星のいずれかの値を使用できます（冥王星を含む）。

赤道半径と極半径を明示的に指定するメソッドを使用する場合、追加の必須引数は次のとおりです：

  * `equatorial_radius`: 物体の赤道半径の値（キロメートル単位）。
  * `polar_radius`: 物体の極半径の値（キロメートル単位）。

代わりに、惑星の選択を使用するメソッドを使用する場合、唯一の追加引数は惑星名です：

  * `planet`（オプションの文字列引数）：太陽系の惑星の名前を含む文字列（「水星」から「冥王星」まで）。省略した場合（つまり、`latitude`、`longitude`、および `altitude` のみが提供される場合）、デフォルトは「地球」です。

すべての場合において、3つの座標は3タプル `(latitude, longitude, altitude)` として渡すことができます。さらに、地理的な `latitude`、`longitude`、および `altitude` は同じ長さの配列として与えることができます。

### 出力

指定された赤道半径と極半径を持つ物体の測地座標における3タプル `(latitude, longitude, altitude)`（デフォルトは地球）。

地理的座標が配列として与えられた場合、同じ長さの配列の3タプルが返されます。

### 方法

Stephen P. Keeler と Yves Nievergelt, "Computing geodetic coordinates", SIAM Rev. Vol. 40, No. 2, pp. 300-309, June 1998 (DOI:[10.1137/S0036144597323921](http://dx.doi.org/10.1137/S0036144597323921))。

惑星定数は Planetary Fact Sheet から取得されています (http://nssdc.gsfc.nasa.gov/planetary/factsheet/index.html)。

### 例

地球の地理的北極（緯度: 90°, 経度: 0°, 高度 0 km）を測地座標で特定します：

```jldoctest
julia> using AstroLib

julia> geo2geodetic(90, 0, 0)
(90.0, 0.0, 21.38499999999931)
```

同様に木星の場合：

```jldoctest
julia> using AstroLib

julia> geo2geodetic(90, 0, 0, "Jupiter")
(90.0, 0.0, 4638.0)
```

赤道半径 8724.32 km および極半径 8619.19 km を持つ惑星上の地理的座標（緯度、経度、高度）= (43.16°, -24.32°, 3.87 km) の測地座標を求めます：

```jldoctest
julia> using AstroLib

julia> geo2geodetic(43.16, -24.32, 3.87, 8724.32, 8619.19)
(43.849399515234516, -24.32, 53.53354478670965)
```

### 注意事項

測地座標から地理座標への変換は正確な解析式で与えられますが、地理座標から測地座標への変換はそうではありません。近似的な反復（ここで使用されているもの）は存在しますが、偏心率と高度が増すにつれて精度が低下する傾向があります。このルーチンで使用される式は、地球に似たまたはそれ以下の偏心率を持つ楕円体（惑星）に対して、すべての空間位置で6桁の正確な結果を提供するはずです。より正確な結果は、非決定的な反復回数を必要とする微積分を通じて得ることができます。

いずれにせよ、測地的（または惑星的）座標から地理的座標に変換する `geodetic2geo` 関数を使用して、`geo2geodetic` の精度を推定できます。

```jldoctest
julia> using AstroLib

julia> collect(geodetic2geo(geo2geodetic(67.2, 13.4, 1.2))) - [67.2, 13.4, 1.2]
3-element Vector{Float64}:
 -3.5672513831741526e-9
  0.0
  9.484211194177306e-10
```

この関数のコードは IDL Astronomy User's Library に基づいています。 ```
