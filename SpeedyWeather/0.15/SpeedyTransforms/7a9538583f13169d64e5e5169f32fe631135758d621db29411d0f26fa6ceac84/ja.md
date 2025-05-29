```julia
∇(
    p::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    kwargs...
) -> Tuple{Any, Any}

```

既存の `SpectralTransform` `S` を使用して `p` の経度方向および緯度方向の勾配を計算します。単位球体上で作用し、`radius` キーワード引数が提供されない限り、1/半径のスケーリングを省略します。
