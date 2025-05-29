```julia
streamplot!(
    ctx::Union{Nothing, Dict{Symbol, Any}},
    grid::ExtendableGrids.ExtendableGrid,
    func;
    kwargs...
)

```

区分線形ベクトル場をストリームプロットとしてプロットします。（2D pyplot のみ）
