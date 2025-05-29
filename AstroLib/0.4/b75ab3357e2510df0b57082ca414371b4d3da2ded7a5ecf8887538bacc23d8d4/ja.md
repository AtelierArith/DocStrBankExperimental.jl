```
eq2hor(ra, dec, jd[, obsname; ws=false, B1950=false, precession=true, nutate=true,
       aberration=true, refract=true, pressure=NaN, temperature=NaN]) -> alt, az, ha

eq2hor(ra, dec, jd, lat, lon[, altitude=0; ws=false, B1950=false,
       precession=true, nutate=true, aberration=true, refract=true,
       pressure=NaN, temperature=NaN]) -> alt, az, ha
```

### 目的

天体 (ra-dec) 座標をローカル水平座標 (alt-az) に変換します。

### 説明

このコードは赤道 (ra,dec) 座標から水平 (alt,az) 座標を計算します。歳差、歳差、光の屈折、屈折の補正を行います。

### 引数

この関数には2つの基本メソッドがあります。1つは、`AstroLib.observatories` に存在する場合、観測所の名前を指定できます。もう1つは、観測地点の座標を提供し、オプションで高度を指定できます。

共通の必須引数:

  * `ra`: 天体の赤経、度単位
  * `dec`: 天体の赤緯、度単位
  * `jd`: ユリウス日

その他の位置引数:

  * `obsname`: `AstroLib.observatories` にある有効な観測所名を設定します。

または

  * `lat`: 場所の北緯、度単位。
  * `lon`: 場所のAST経度、度単位。西経は負の符号で指定できます。
  * `altitude`: 観測地点の高度、メートル単位。デフォルトは `0` です。

オプションのキーワード引数:

  * `ws` (オプションのブールキーワード): 南から西に測定された方位角を取得するには `true` に設定します（北の東ではありません）
  * `B1950` (オプションのブールキーワード): ra と dec が J2000 (FK5) ではなく B1950 (FK4 座標) で指定されている場合は `true` に設定します。デフォルトは `false` です。
  * `precession` (オプションのブールキーワード): 前進補正を行わない場合は `false` に設定します。デフォルトは `true` です。
  * `nutate` (オプションのブールキーワード): 年周運動を行わない場合は `false` に設定します。デフォルトは `true` です。
  * `aberration` (オプションのブールキーワード): 光の屈折補正を行わない場合は `false` に設定します。デフォルトは `true` です。
  * `refract` (オプションのブールキーワード): 屈折補正を行わない場合は `false` に設定します。デフォルトは `true` です。
  * `pressure` (オプションのキーワード): 観測地点の圧力、ミリバール単位。デフォルト値は `NaN` です。
  * `temperature` (オプションのキーワード): 観測地点の温度、ケルビン単位。デフォルト値は `NaN` です。

### 出力

  * `alt`: 水平座標の高度、度単位
  * `az`: 北から東に測定された方位角（ws が `true` の場合を除く）、度単位
  * `ha`: 時間角、度単位

### 例

```jldoctest
julia> using AstroLib

julia> alt_o, az_o = eq2hor(ten(6,40,58.2)*15, ten(9,53,44), 2460107.25, ten(50,31,36),
                            ten(6,51,18), 369, pressure = 980, temperature=283)
(16.423991509721567, 265.60656932130564, 76.11502253130612)

julia> adstring(az_o, alt_o)
" 17 42 25.6  +16 25 26"
```

### 注意事項

この関数のコードは IDL 天文学ユーザーライブラリに基づいています。
