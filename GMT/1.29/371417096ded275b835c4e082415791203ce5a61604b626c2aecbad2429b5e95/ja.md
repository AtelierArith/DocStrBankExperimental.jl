```
grat = graticules(D, width=(30,20), grid=nothing, annot_x=nothing)
```

または

```
grat = graticules(; proj="projection", width=(30,20), pm=0, grid=nothing, annot_x=nothing)
```

`width`間隔で子午線と緯線を持つ投影グラティキュールGMTdatasetを作成します。

  * `D`: 投影情報を保持するGMTdataset（またはそれらのベクトル）。この引数はGMTdataset型の代わりに参照されたグリッドまたは画像型であることもできます。
  * `proj`: 代わりに投影を説明するproj4文字列またはシンボルを渡します。
  * `pm`: 投影の本初子午線（デフォルトは0またはD.proj4にあるもの）。
  * `width`: 経度と緯度の増分を持つスカラーまたは2要素の配列/タプル。スカラーの場合、width*x = width*y。
  * `grid`: 自動的なグラティキュールのセットを生成する`width`引数の代わりに、作成する子午線（grid[1]）と緯線（grid[2]）を持つ2要素のVector{Vector{Real}}を渡すことができます。
  * `annot_x`: デフォルトでは、`plotgrid!`関数で`grat`が使用されるとすべての子午線が注釈されますが、投影と`worldrectangular`で使用される`latlim`引数によっては、本初子午線付近で経度ラベルが重なることがあります。それを最小限に抑えるために、注釈を付ける経度のベクトルを渡します。*例* `annot_x=[-180,-150,0,150,180]`はこれらの経度のみを注釈します。

### 戻り値

投影された子午線と緯線を含むGMTdatasetのベクトル。`grat[i]`属性はその要素のlon,latに関する情報を格納します。

### 例

```
grat = graticules(proj="+proj=ob_tran +o_proj=moll +o_lon_p=40 +o_lat_p=50 +lon_0=60");
```
