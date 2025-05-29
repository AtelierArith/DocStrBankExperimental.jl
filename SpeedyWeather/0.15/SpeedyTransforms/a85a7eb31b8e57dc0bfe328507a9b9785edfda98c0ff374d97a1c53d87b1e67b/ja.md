```julia
∇(
    p::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Tuple{Any, Any}

```

`p`の緯度方向および経度方向の勾配。`SpectralTransform` `S`を事前計算します。単位球体上で作用し、`radius`キーワード引数が提供されない限り1/半径のスケーリングを省略します。
