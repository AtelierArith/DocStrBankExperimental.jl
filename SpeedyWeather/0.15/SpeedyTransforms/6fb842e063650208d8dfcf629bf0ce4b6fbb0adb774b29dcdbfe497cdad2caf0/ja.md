```julia
∇²(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Any

```

入力 `alms` に適用されるラプラス演算子 ∇² を返します。単位球に作用し、`radius` キーワード引数が提供されない限り 1/radius^2 のスケーリングを省略します。
