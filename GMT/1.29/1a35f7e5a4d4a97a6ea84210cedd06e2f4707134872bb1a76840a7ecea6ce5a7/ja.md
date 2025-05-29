```
grat = worldrectgrid(GI; width=(30,20), grid=nothing, annot_x=nothing)
```

または

```
grat = worldrectgrid(; proj="projection", width=(30,20), grid=nothing, annot_x=nothing)
```

投影座標系での線のグリッド（グラティキュール）を作成します。投影システムは`GI`メタデータから抽出されます。

  * `GI`: `worldrectangular`関数で作成されたGMTgridまたはGMTimageデータ型。
  * `proj`: 投影を説明するproj4文字列またはシンボルを渡します。あるいは、投影が抽出される参照GMTdatasetを渡します。
  * `width`: 経度と緯度の増分を持つスカラーまたは2要素の配列/タプル。スカラーの場合、width*x = width*yです。
  * `grid`: 自動的なグラティキュールのセットを生成する`width`引数の代わりに、経線（grid[1]）と緯線（grid[2]）を作成するための2要素のVector{Vector{Real}}を渡すことができます。
  * `annot_x`: デフォルトでは、`plotgrid!`関数で`grat`が使用されるとすべての経線が注釈されますが、投影や`worldrectangular`で使用される`latlim`引数によっては、プライム経線付近で経度ラベルが重なることがあります。それを最小限に抑えるために、注釈を付ける経度のベクトルを渡します。*例* `annot_x=[-180,-150,0,150,180]`は、これらの経度のみを注釈します。

### 戻り値

投影された経線と緯線を含むGMTdatasetのベクトル。`grat[i]`属性は、その要素のlon,latに関する情報を格納します。
