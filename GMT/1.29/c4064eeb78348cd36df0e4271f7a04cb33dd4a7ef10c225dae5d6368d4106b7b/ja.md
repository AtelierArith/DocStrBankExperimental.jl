```
rasterzones!(GI::GItype, shapes::Vector{GMTdataset}, fun::Function; touches=false, byfeatures::Bool=false, groupby="")
```

または

```
rasterzones!(fun::Function, GI::GItype, shapes::Vector{GMTdataset}; touches=false, byfeatures::Bool=false, groupby="")
```

一様な関数 `fun` を、GMTdataset `shapes` のポリゴン内にあるグリッドまたは画像 `GI` の要素に適用します。`GI` 配列はその場で修正されます。

### 引数

  * `GI`: `fun` を適用して `shapes` のポリゴン内にある要素を修正するグリッド (GMTgrid) または画像 (GMTimage) タイプ。
  * `shapes`: `GI` の要素が `fun` を適用することで得られる単一の値に割り当てられるポリゴンを含む GMTdataset のベクター。
  * `fun`: `shapes` の各ポリゴン内にある `GI` 要素の定数値を計算するために使用される一様な関数名。

### パラメータ

  * `touches`: ポリゴンに触れたすべてのセル/ピクセルを含めます。デフォルトは、ポリゴン内に中心があるセルのみを含めることです。
  * `byfeatures`: OGR ベクターファイル (shapes, geopackages, arrow など) から読み込まれたデータセットは、各々が複数のジオメトリを含む可能性のあるフィーチャに整理されます。フィーチャ内のジオメトリの各グループは、同じ `Feature_ID` 属性を共有します。`byfeatures` が true の場合、関数 `fun` は各フィーチャに独立して適用されます。このオプションは実際には `groupby` パラメータに似ていますが、属性名は必要ありません。`byfeatures` または `groupby` のいずれも提供されない場合、`fun` 関数は各ポリゴンに独立して適用されます。
  * `groupby`: 提供される場合、属性名でなければなりません。例えば、`groupby="NAME"` のように。提供されない場合、OGR ファイルの読み込み中に割り当てられた一意の識別子である `Feature_ID` 属性が使用されます。`byfeatures` または `groupby` のいずれも提供されない場合、`fun` 関数は各ポリゴンに独立して適用されます。

参照: `colorzones!`

### 戻り値

何も返しませんが、入力 `GI` は修正されます。

## 例

```
ピークグリッドを取得し、中央の三角形内にある要素をその平均値で置き換えます。

G = GMT.peaks();
D = mat2ds([-1 -1; 0 1; 1 -1; -1 -1]);
rasterzones!(G, D, mean)
```
