```
function geodesic(D; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0, longest::Bool=false)
```

または

```
function geodesic(lon1, lat1, lon2, lat2; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0, longest::Bool=false)
```

楕円体上の測地線を生成します（最短距離）。入力データは2点以上である必要があります。後者の場合、各線分は`step`の増分で離散化されます。

### パラメータ

  * `D`: - 入力点。これはGMTdataset（またはそのベクトル）、Mx2行列、`gmtread()`でGMTdatasetとして読み取れるファイル名、またはGDAL AbstractDatasetオブジェクトのいずれかです。
  * `step`: - セグメント線がメートル（デフォルト）で離散化される増分距離ですが、`unit`を参照してください。
  * `unit`: - `step`がメートルでない場合は、`unit=:km`、`unit=:Nautical`、または`unit=:Miles`のいずれかを使用します。
  * `np`:   - ポリラインの頂点間の中間点の数（`step`の代替）。
  * `proj`  - 線データが直交座標系にあるが、既知の投影がある場合はPROJ4文字列を渡します。
  * `epsg`  - `proj`と同じですが、EPSGコードを使用します。
  * `longest` - 測地線の「長い道のり」を計算します。つまり、A点からB点に行く際に最も長い経路を取ります。ただし、子午線や赤道以外の測地線は閉じた経路ではないことに注意してください（https://en.wikipedia.org/wiki/Geodesics*on*an*ellipsoidを参照）。この線は、AからBへの方位を計算し、Bでその方位で線を開始し、地球を一周して、Aに「近い」地点に到達するまで進みますが、正確にはAには到達しません（単純な子午線の場合を除く）。

### 戻り値

入力が行列の場合、測地線に沿った点のlon latを持つMx2行列。GMTデータセットまたはそのベクトル（入力がVector{GMTdataset}の場合）。

## 例: 点(0,0)と(30,50)の間の測地線を100 kmのステップで計算します。

```
mat = geodesic([0 0; 30 50], step=100, unit=:k);
```
