```julia
∇²(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    kwargs...
) -> Any

```

ラプラス演算子 ∇² が入力 `alms` に適用され、`S` からの事前計算された固有値を使用します。単位球面上で作用し、`radius` キーワード引数が提供されない限り、1/radius^2 のスケーリングを省略します。
