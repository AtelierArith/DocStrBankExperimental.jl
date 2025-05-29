```julia
scalarplot(
    grid::ExtendableGrids.ExtendableGrid,
    func;
    Plotter,
    kwargs...
) -> Any

```

グリッド上にノードベクトルをP1 FEM関数として三角形分割でプロットします。

ノードベクトルの代わりに関数が与えられた場合、それはグリッド上で評価されます。

グリッドの代わりに座標のベクトルが与えられた場合、自動的にグリッドが作成されます。

キーワード引数については、[`available_kwargs`](@ref)を参照してください。
