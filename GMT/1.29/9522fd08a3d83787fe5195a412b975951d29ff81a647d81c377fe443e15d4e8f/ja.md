```
function loxodrome(lon1,lat1,lon2,lat2; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0)
```

または

```
function loxodrome(D; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0)
```

楕円体上にロクソドローム（リブライン）を生成します。入力データは2点以上のポイントを含むことができます。後者の場合、各線分は`step`の増分で離散化されます。

### パラメータ

  * `D`: - 入力ポイント。これは2x2の行列またはGMTdatasetのいずれかです。最初の2ポイントのみが使用されることに注意してください。
  * `step`:  - セグメントラインがメートル（デフォルト）で離散化される増分距離ですが、`unit`を参照してください。
  * `unit`:  - `step`がメートルでない場合は、`unit=:km`、`unit=:Nautical`、または`unit=:Miles`のいずれかを使用します。
  * `np`:    - 終点間に生成される中間ポイントの数（`step`の代替）。
  * `proj`  - 線データが直交座標系にあるが、既知の投影がある場合はPROJ4文字列を渡します。
  * `epsg`  - `proj`と同じですが、EPSGコードを使用します。

### 戻り値

入力が行列または2組のポイントの場合、ロクソドロームに沿ったポイントの緯度を持つMx2行列。入力がGMTdatasetの場合はGMTdataset。

## 例：ポイント(0,0)と(30,50)の間のロクソドロームを100 kmのステップで計算します。

```
loxo = loxodrome([0 0; 30 50], step=100, unit=:k);
```
