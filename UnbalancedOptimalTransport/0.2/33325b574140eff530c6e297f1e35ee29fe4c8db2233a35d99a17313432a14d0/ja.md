```
function optimal_coupling!(
    D::AbstractDivergence,
    C,
    a::DiscreteMeasure,
    b::DiscreteMeasure,
    ϵ = 1e-1;
    dual_potentials_populated::Bool = false,
    kwargs...) -> Matrix
```

`a` と `b` の最適なカップリングを、最適な双対ポテンシャル、正則化パラメータ `ϵ`、およびコスト関数 `C` を使用して計算します。

`dual_potentials_populated = false` の場合、[`unbalanced_sinkhorn!`](@ref) が呼び出され、発散 `D` を使用して `a` と `b` の双対ポテンシャルが設定されます。`dual_potentials_populated = true` の場合、最適な双対ポテンシャルを設定するために、[`unbalanced_sinkhorn!`](@ref) または [`OT!`](@ref) または [`sinkhorn_divergence!`](@ref) のいずれかが最初に呼び出される必要があり、同じ `ϵ` と `C` の選択が必要です。この場合、`a` と `b` は変更されません。

この関数は [[SFVTP19](@ref)] の命題 6 を実装しています。
