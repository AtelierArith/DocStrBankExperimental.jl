```julia
transform(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    unscale_coslat,
    kwargs...
) -> Any

```

球面係数 `alms` から新しく割り当てられたグリッドフィールド `map` へのスペクトル変換（スペクトルからグリッド空間へ）。`alms` のサイズに基づいて、グリッドタイプ `grid` に対して、空間解像度は `grid` に対して定義された切り捨てに基づいて取得されます。スペクトル変換構造体 `S` が割り当てられ、`transform(alms, S)` を実行します。
