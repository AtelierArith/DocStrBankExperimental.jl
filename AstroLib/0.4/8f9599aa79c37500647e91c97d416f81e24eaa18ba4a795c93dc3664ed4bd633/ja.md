```
premat(equinox1, equinox2[, FK4=true]) -> precession_matrix
```

### 目的

`equinox1` から `equinox2` への歳差行列を返します。

### 説明

この行列は、天文座標を歳差させるために `precess` および `baryvel` によって使用されます。

### 引数

  * `equinox1`: 座標の元の等分点。
  * `equinox2`: 歳差された座標の等分点。
  * `FK4` (オプションのブールキーワード): このキーワードが `true` に設定されている場合、FK4 (B1950.0) システムの歳差角が歳差行列の計算に使用されます。`false` の場合、デフォルトで FK5 (J2000.0) の歳差角が使用されます。

### 出力

赤道直交座標を歳差させるために使用される 3×3 行列。

### 例

FK4 システムで 1950.0 から 1975.0 への歳差行列を返します。

```jldoctest
julia> using AstroLib

julia> premat(1950, 1975, FK4=true)
3×3 StaticArraysCore.SMatrix{3, 3, Float64, 9} with indices SOneTo(3)×SOneTo(3):
 0.999981    -0.00558775  -0.00242909
 0.00558775   0.999984    -6.78691e-6
 0.00242909  -6.78633e-6   0.999997
```

### 方法

FK4 定数は Taff (1983) の「Computational Spherical Astronomy」p. 24 から。 (FK4)。 FK5 定数は「Explanatory Supplement To The Astronomical Almanac」1992年、ページ104 表3.211.1 から (https://archive.org/details/131123ExplanatorySupplementAstronomicalAlmanac)。

### 注意事項

この関数のコードは IDL Astronomy User's Library に基づいています。
