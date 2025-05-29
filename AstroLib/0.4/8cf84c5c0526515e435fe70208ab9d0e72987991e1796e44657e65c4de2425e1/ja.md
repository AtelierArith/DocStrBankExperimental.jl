```
hor2eq(alt, az, jd[, obsname;
       ws=false, B1950=false, precession=true, nutate=true,
       aberration=true, refract=true,
       lat=NaN, lon=NaN, altitude=0,
       pressure=NaN, temperature=NaN]) -> ra, dec, ha

hor2eq(alt, az, jd, lat, lon[, altitude=0;
       ws=false, B1950=false, precession=true, nutate=true,
       aberration=true, refract=true,
       pressure=NaN, temperature=NaN]) -> ra, dec, ha
```

### 目的

地平座標（alt-az）を赤道座標（ra-dec）に変換します。

### 説明

これは、地平座標（alt,az）から赤道座標（ra,dec）を計算する関数です。約1秒角またはそれ以上の精度があります。歳差、歳差、光の屈折、屈折の補正を行います。

### 引数

この関数には2つの基本メソッドがあります。1つは、`AstroLib.observatories`に存在する場合、観測所の名前を指定できます。もう1つは、観測地点の座標を提供し、オプションで高度を指定できます。

共通の必須引数：

  * `alt`: 地平座標の高度（度）
  * `az`: 北から東に測定された方位角（wsが`true`でない限り）（度）
  * `jd`: ユリウス日

その他の位置引数：

  * `obsname`: `AstroLib.observatories`にある有効な観測所名を設定します。

または

  * `lat`: 場所の北緯（度）。
  * `lon`: 場所のAST経度（度）。西経度は負の符号で指定できます。
  * `altitude`: 観測地点の高度（メートル）。デフォルトは`0`です。

オプションのキーワード引数：

  * `ws`（オプションのブールキーワード）：南から西に測定された方位角を取得するには、これを`true`に設定します。デフォルトは`false`です。
  * `B1950`（オプションのブールキーワード）：raとdecがB1950（FK4座標）で指定されている場合は、これを`true`に設定します。デフォルトは`false`です。
  * `precession`（オプションのブールキーワード）：歳差なしにするには、これを`false`に設定します。デフォルトは`true`です。
  * `nutate`（オプションのブールキーワード）：歳差なしにするには、これを`false`に設定します。デフォルトは`true`です。
  * `aberration`（オプションのブールキーワード）：光の屈折補正なしにするには、これを`false`に設定します。デフォルトは`true`です。
  * `refract`（オプションのブールキーワード）：屈折補正なしにするには、これを`false`に設定します。デフォルトは`true`です。
  * `pressure`（オプションのキーワード）：観測地点の圧力（ミリバール）。デフォルト値は`NaN`です。
  * `temperature`（オプションのキーワード）：観測地点の温度（ケルビン）。デフォルト値は`NaN`です。

### 出力

  * `ra`: 天体の赤経（度）（FK5）
  * `dec`: 天体の赤緯（度）（FK5）
  * `ha`: 時間角（度）

### 例

あなたはキットピーク国立天文台にいて、方位角264d 55m 06s、高度37d 54m 41s（可視範囲内）の星を見ています。今日は2041年12月25日で、現地時間はちょうど午後10時です。あなたが見ている星の赤経と赤緯（J2000）は何ですか？ここでの温度は約0度セルシウスで、圧力は781ミリバールです。この時のユリウス日は2466879.7083333です。

```jldoctest
julia> using AstroLib

julia> ra_o, dec_o = hor2eq(ten(37,54,41), ten(264,55,06), 2466879.7083333,
                            "kpno", pressure = 781, temperature = 273)
(3.3224480269254713, 15.19061543702944, 54.61174536229464)

julia> adstring(ra_o, dec_o)
" 00 13 17.4  +15 11 26"
```

### 注意

この関数のコードはIDL天文学ユーザーライブラリに基づいています。 ```
