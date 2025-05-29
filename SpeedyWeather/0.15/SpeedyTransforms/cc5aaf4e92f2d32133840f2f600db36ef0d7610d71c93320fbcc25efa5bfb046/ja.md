```julia
transform(
    grids::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

`grids` から新しく割り当てられた `LowerTriangularArray` へのスペクトル変換（グリッドからスペクトル空間）。`grids` のサイズとキーワード `dealiasing` に基づいて、スペクトル解像度の切り捨てが取得されます。スペクトル変換構造体 `S` が割り当てられ、`transform(grids, S)` を実行します。
