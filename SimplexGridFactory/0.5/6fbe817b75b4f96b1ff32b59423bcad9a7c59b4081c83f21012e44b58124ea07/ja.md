```julia
simplexgrid(
    ::Type{SimplexGridFactory.TetGenType},
    TetGen,
    input;
    kwargs...
) -> ExtendableGrids.ExtendableGrid

```

TetGenデータからグリッドを作成します。

利用可能な`kwargs`については[`default_options`](@ref)を参照してください。
