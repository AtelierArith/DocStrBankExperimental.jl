```
zonal_statistics(GI::GItype, shapes::GDtype, fun::Function; touches=false, byfeatures=false, groupby="")
```

または

```
zonal_statistics(fun::Function, GI::GItype, shapes::GDtype; touches=false, byfeatures=false, groupby="")
```

または `zonal_stats(...)`

`shapes` のポリゴン内にあるグリッドまたは画像 `GI` の要素に適用された `fun` の統計を計算します。

### 引数

  * `GI`: 統計が計算されるグリッド (GMTgrid) または画像 (GMTimage) タイプで、`shapes` のポリゴン内にある要素に `fun` 関数を適用します。
  * `shapes`: `GI` の要素が `fun` 関数を適用することによって単一の値を割り当てられるポリゴンを含む GMTdataset のベクターです。
  * `fun`: `shapes` の各ポリゴン内にある `GI` 要素の定数値を計算するために使用される一元関数の名前です。

### パラメータ

  * `touches`: ポリゴンに触れたすべてのセル/ピクセルを含めます。デフォルトは、ポリゴン内に中心があるセルのみを含めることです。
  * `byfeatures`: OGRベクターファイル (shapes, geopackages, arrow など) から読み込まれたデータセットは、複数のジオメトリを含む可能性のあるフィーチャに整理されます。フィーチャ内のジオメトリの各グループは、同じ `Feature_ID` 属性を共有します。`byfeatures` が true の場合、関数 `fun` は各フィーチャに独立して適用されます。このオプションは実際には `groupby` パラメータに似ていますが、属性名は必要ありません。`byfeatures` または `groupby` のいずれも提供されない場合、`fun` 関数は各ポリゴンに独立して適用されます。
  * `groupby`: 提供される場合、属性名でなければなりません。例えば、`groupby="NAME"` のように。提供されない場合、OGRファイルの読み込み中に割り当てられた一意の識別子である `Feature_ID` 属性が使用されます。`byfeatures` または `groupby` のいずれも提供されない場合、`fun` 関数は各ポリゴンに独立して適用されます。

### 例

スイスの平均標高は何ですか？

```julia
G = gmtread("@earth_relief_06m");
Swiss = coast(DCW=:CH, dump=true, minpts=50);
zonal_statistics(G, Swiss, mean)

1×1 GMTdataset{Float64, 2}
 Row │       X
─────┼─────────
   1 │ 1313.21
```
