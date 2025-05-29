```julia
∇!(
    dpdx::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    dpdy::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    p::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    radius
) -> Tuple{SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray}

```

入力 `p` に対して勾配演算子 ∇ を適用し、その結果を `dpdx`（経度方向の導関数）および `dpdy`（緯度方向の導関数）に格納します。勾配演算子は単位球面上で作用し、したがって `radius` キーワード引数が提供されない限り 1/radius のスケーリングを省略します。
