```
refine(
    spline_grid::A,
    dim_refinement::Integer;
    knots_new::Union{AbstractVector{<:AbstractFloat}, Nothing} = nothing)::Tuple{A, RefinementMatrix} where {A <: AbstractSplineGrid}
```

指定されたスプライン次元に基づいて、ノットベクトルに複数のノットを追加する新しいスプライングリッドを作成します。

## 入力

  * `spline_grid`: どのノットベクトルが洗練されるかを示すスプライングリッド
  * `dim_refinement`: ノットベクトルが洗練されるスプライン次元のインデックス
  * `knots_new`: 追加されるノット。デフォルトは`nothing`で、これは内部的に洗練されるノットベクトルの非自明なノットスパンのすべての中点に変換されます。

## 出力

  * `spline_grid_new`: 更新されたノットベクトルと制御点を除いて、すべて同じ基盤メモリを持つ新しく作成されたスプライングリッド。
  * `refinement_matrix`: ノット挿入次元のノット挿入前の基底関数をノット挿入後の基底関数で表現する疎行列。
