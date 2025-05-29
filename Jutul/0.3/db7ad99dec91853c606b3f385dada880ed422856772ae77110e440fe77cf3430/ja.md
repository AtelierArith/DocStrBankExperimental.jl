```
CartesianMesh(dims, [Δ, [origin]])
```

指定された `Tuple` `dims` によって次元を持つ直交メッシュを作成します。

# 引数

  * `dims::Tuple`: 各方向のグリッドセルの数。例えば、`(nx, ny)` は x方向に `nx` セルを持つ2Dグリッドを生成します。
  * `Δ::Tuple=Tuple(ones(length(dims)))`: `dims` と同じ長さ。第一のオプション: 各エントリがその方向の各セルの長さであるスカラーの `Tuple`。例えば、各グリッドセルが面積 `Δx*Δy` を持つ均一グリッドのために `(Δx, Δy)` を指定します。第二のオプション: 各エントリがその方向のセルサイズを含むベクトルの `Tuple`。
  * `origin=zeros(length(dims))`: グリッドの最初のコーナーの原点。

# 例

2 by 3 by 5 ユニットの領域を離散化する均一な3Dメッシュを生成します。3 by 5 by 2 セルを持ちます：

```julia-repl
julia> CartesianMesh((3, 5, 2), (2.0, 3.0, 5.0))
CartesianMesh (3D) with 3x5x2=30 cells
```

非均一な2Dメッシュを生成します：

```julia-repl
julia> CartesianMesh((2, 3), ([1.0, 2.0], [0.1, 3.0, 2.5]))
CartesianMesh (2D) with 2x3x1=6 cells
```
