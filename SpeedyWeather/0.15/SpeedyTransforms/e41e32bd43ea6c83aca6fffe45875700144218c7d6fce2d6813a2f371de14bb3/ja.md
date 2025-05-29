```julia
∇⁻²(
    ∇²alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Any

```

入力 `alms` に適用される逆ラプラス演算子 ∇⁻² を返します。単位球面上で作用し、`radius` キーワード引数が提供されない限り、半径^2 のスケーリングを省略します。
