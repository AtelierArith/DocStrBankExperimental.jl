triplot(in::Matrix; onlyedges::Bool=false, noplot::Bool=false, kw...)

2-Dの三角分割または与えられた行列の点によって定義されたボロノイ多角形をプロットします。

### 引数

  * `in`: 入力データ。Mx2またはMx3の行列である必要があります。

### キーワード引数

  * `noplot`: プロットする代わりに計算されたデローニーまたはボロノイデータを返します（デフォルト）。
  * `onlyedges`: デフォルトでは、デローニー三角形またはボロノイセルを多角形として計算します。このオプションを `onlyedges=true` として使用すると、複数の線分を計算します。
  * `region`: `voronoi` のためのデータ領域 (xmin,xmax,ymin,ymax) を設定します（必須）。提供されない場合は、`in` から計算します。
  * `voronoi`: デローニー三角形の代わりにボロノイセルを計算します（`region` が必要です）。
  * `kw...`: $plot$ モジュールで使用されるキーワード引数（`noplot=true` の場合は無視します）。

### 戻り値

`noplot=true` の場合は GMTdataset、そうでない場合は $nothing$ を返します。

### 例:

```julia
triplot(rand(5,2), voronoi=true, show=true)

triplot(rand(5,3), lc=:red, show=true)
```
