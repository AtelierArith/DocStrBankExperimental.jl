```julia
bedgemask!(
    grid::ExtendableGrids.ExtendableGrid,
    xa,
    xb,
    ireg::Int64;
    tol
) -> ExtendableGrids.ExtendableGrid

```

グリッド境界エッジの領域番号をラインマスクを介して編集します。これは3Dグリッドにのみ適用されます。
