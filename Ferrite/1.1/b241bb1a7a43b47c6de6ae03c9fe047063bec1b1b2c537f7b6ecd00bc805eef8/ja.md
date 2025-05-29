```
create_coloring(g::Grid, cellset=1:getncells(g); alg::ColoringAlgorithm)
```

グリッド `g` のセルに色付けを行い、隣接するセルが同じ色にならないようにします。色付けするセルのサブセットのみを指定する場合は、`cellset` で色付けするセルを指定できます。

セルのインデックスを持つベクトルのベクトルを返します。例えば：

```julia
ret = [
   [1, 3, 5, 10, ...], # 色1のセル
   [2, 4, 6, 12, ...], # 色2のセル
]
```

利用可能な2つの異なるアルゴリズムがあり、`alg` キーワード引数で指定します：

  * `alg = ColoringAlgorithm.WorkStream` (デフォルト)：Turcksin et al. [Turcksin2016](@cite) による3ステップアルゴリズムですが、2ステップ目では貪欲な色付けが行われます。一般的に `ColoringAlgorithm.Greedy` よりも多くの色が生成されますが、セルは色の間でより均等に分配されます。
  * `alg = ColoringAlgorithm.Greedy`：構造化された四角形グリッド（例えば、`generate_grid` からの四角形グリッド）に対してうまく機能する貪欲アルゴリズムです。

結果の色は [`Ferrite.write_cell_colors`](@ref) を使用して視覚化できます。

!!! note "色付けするセルのマッピング"
    Ferrite の以前のバージョンでは、この関数はセル ID を色番号にマッピングする辞書を最初の引数として返しました。このマッピングが必要な場合は、次の構文を使用して作成できます：

    ```julia
    colors = create_coloring(...)
    cell_colormap = Dict{Int,Int}(
        cellid => color for (color, cellids) in enumerate(final_colors) for cellid in cellids
    )
    ```


# 参考文献

  * [Turcksin2016](@cite) Turcksin et al. ACM Trans. Math. Softw. 43 (2016).
