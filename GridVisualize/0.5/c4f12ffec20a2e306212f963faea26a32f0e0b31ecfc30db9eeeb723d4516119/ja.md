```julia
scalarplot!(
    ctx::Union{Nothing, Dict{Symbol, Any}},
    grid::ExtendableGrids.ExtendableGrid,
    func;
    kwargs...
)

```

グリッド上にノードベクトルをP1 FEM関数としてプロットし、視覚化ツールのサブプロットに三角形分割を表示します。`[i,j]`が省略された場合、`[1,1]`が仮定されます。

ノードベクトルの代わりに関数が与えられた場合、それはグリッド上で評価されます。

グリッドの代わりに座標ベクトルが与えられた場合、一時的なグリッドが作成されます。

キーワード引数: [`available_kwargs`](@ref)を参照してください。
