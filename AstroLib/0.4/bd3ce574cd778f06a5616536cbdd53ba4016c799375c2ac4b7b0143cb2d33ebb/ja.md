```
precess(ra, dec, equinox1, equinox2[, FK4=true, radians=true]) -> prec_ra, prec_dec
```

### 目的

`equinox1` から `equinox2` へ座標を歳差させます。

### 説明

デフォルトの `(ra, dec)` システムは、エポック J2000.0 に基づく FK5 ですが、B1950.0 に基づく FK4 が `FK4` ブールキーワードを介して利用可能です。

### 引数

  * `ra`: 入力の赤経、スカラーまたはベクトル、度単位。`radians` キーワードが `true` に設定されていない限り。
  * `dec`: 入力の赤緯、スカラーまたはベクトル、度単位。`radians` キーワードが `true` に設定されていない限り。
  * `equinox1`: 座標の元の等時点、数値スカラー。
  * `equinox2`: 歳差された座標の等時点。
  * `FK4` (オプションのブールキーワード): このキーワードが `true` に設定されている場合、FK4 (B1950.0) システムの歳差角が歳差行列の計算に使用されます。`false` の場合、デフォルトとして FK5 (J2000.0) の歳差角を使用します。
  * `radians` (オプションのブールキーワード): このキーワードが `true` に設定されている場合、入力および出力の赤経と赤緯のベクトルは度ではなくラジアンで表されます。

### 出力

歳差によって修正された座標の 2 組 `(ra, dec)`。

### 例

ポールスターの J2000.0 座標は (2h, 31m, 46.3s, 89d 15' 50.6") です。J1985.0 での座標を計算します。

```jldoctest
julia> using AstroLib

julia> ra, dec = ten(2,31,46.3)*15, ten(89,15,50.6)
(37.94291666666666, 89.26405555555556)

julia> adstring(precess(ra, dec, 2000, 1985), precision=1)
" 02 16 22.73  +89 11 47.3"
```

Eps Ind の B1950 座標 (RA = 21h 59m,33.053s, DEC = -56d, 59', 33.053") を等時点 B1975 に歳差させます。

```jldoctest
julia> using AstroLib

julia> ra, dec = ten(21, 59, 33.053) * 15, ten(-56, 59, 33.053)
(329.88772083333333, -56.992514722222225)

julia> adstring(precess(ra, dec, 1950, 1975, FK4=true), precision=1)
" 22 01 15.46  -56 52 18.7"
```

### 方法

Taff (1983) の「Computational Spherical Astronomy」からのアルゴリズム、p. 24. (FK4)。FK5 定数は「Explanatory Supplement To The Astronomical Almanac」1992年、ページ 104 表 3.211.1 から。 (https://archive.org/details/131123ExplanatorySupplementAstronomicalAlmanac)。

### 注意事項

歳差の精度は、赤緯の値が 90 度に近づくにつれて低下します。`precess` は FK5 システムで 2000 年から 2.5 世紀以上使用すべきではありません (FK4 システムでは 1950.0)。より良い精度が必要な場合は、必要に応じて `bprecess` または `jprecess` を使用してください。

この関数のコードは IDL Astronomy User's Library に基づいています。
