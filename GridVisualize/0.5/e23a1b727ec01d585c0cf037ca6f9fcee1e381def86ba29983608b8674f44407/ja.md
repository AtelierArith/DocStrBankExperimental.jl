```julia
streamplot(
    grid::ExtendableGrids.ExtendableGrid,
    func;
    Plotter,
    kwargs...
) -> Any

```

区分線形ベクトル場をストリームプロットとしてプロットします。（2D pyplot のみ）
