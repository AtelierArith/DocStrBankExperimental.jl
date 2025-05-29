```
refine(
    spline_dimension::SplineDimension{Tv, Ti};
    knots_new::Union{Vector{<:AbstractFloat}, Nothing} = nothing)::Tuple{SplineDimension{Tv, Ti}, RefinementMatrix{Tv, Ti}} where {Tv, Ti}
```

新しいノットを基礎となるノットベクトルに追加したスプライン次元を作成します。

## 入力

  * `spline_dimension`: 新しいノットが追加されるスプライン次元
  * `knots_new`: 追加されるノットのベクトル。デフォルトでは、スプライン次元の基礎となるベクトルのノットスパンの中点になります。

## 出力

  * `spline_dimension_new`: 新しいノットベクトルを除いて、同じ基礎メモリを持つ新しく作成されたスプライン次元。
  * `refinement_matrix`: 精緻化前の基底関数を精緻化後の基底関数の観点から表現する疎行列。
