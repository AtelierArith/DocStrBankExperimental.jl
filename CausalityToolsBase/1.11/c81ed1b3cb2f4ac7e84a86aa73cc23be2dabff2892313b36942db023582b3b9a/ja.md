```
generate_gridpoints(points, binning_scheme::RectangularBinning, 
    grid::GridType = OnGrid())
```

`binning_scheme` と `grid` タイプによって指定されたハイパーレクタングルボックスをカバーする矩形グリッドを形成する点のセットを返します。適切なビニングスキームが与えられた場合、このグリッドは `points` のカバーを提供します。詳細については `RectangularBinning` のドキュメントを参照してください。

## 引数

  * **`points`**: 点のベクトルまたは `Dataset` インスタンス。
  * **`binning_scheme`**: `RectangularBinning` インスタンス。
  * **`grid`**: `GridType` インスタンス。グリッドは Interpolations.jl と同じ規則に従います。有効な選択肢は `OnGrid()`（ビンの原点をグリッドポイントとして使用）と `OnCell()`（各軸に沿って追加の区間を加え、グリッドを各軸の外側に半ビンシフトし、結果として得られるグリッドセルの中心を返す）です。

## 例

例えば、

```julia
using CausalityToolsBase, DelayEmbeddings

pts = Dataset([rand(3) for i = 1:100])
generate_gridpoints(pts, RectangularBinning(10), OnGrid()
```

は、各座標軸を10の等長区間に分割することによって構築された `pts` の範囲をカバーする矩形グリッドを生成します。

例えば、

```julia
using CausalityToolsBase, DelayEmbeddings

pts = Dataset([rand(3) for i = 1:100])
generate_gridpoints(pts, RectangularBinning(10), OnCell()
```

は同様のことを行いますが、もう1つの区間（合計11）を追加し、全体のハイパーキューブをシフトして、各軸に沿った最小値と最大値が元の極値の外側に半ビンだけ位置するようにし、グリッドセルの中心を返します。
