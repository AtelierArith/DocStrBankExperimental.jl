```julia
cellmask!(
    grid::ExtendableGrids.ExtendableGrid,
    maskmin,
    maskmax,
    ireg::Int64;
    tol
) -> ExtendableGrids.ExtendableGrid

```

長方形マスクを介してグリッドセルの領域番号を編集します。

例: [Rectangle-with-multiple-regions](@ref)
