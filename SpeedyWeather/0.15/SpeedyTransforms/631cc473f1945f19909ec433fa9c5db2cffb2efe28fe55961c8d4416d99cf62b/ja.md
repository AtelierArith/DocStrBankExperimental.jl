```julia
∇(
    grid::SpeedyWeather.RingGrids.AbstractGridArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    kwargs...
) -> Tuple{Any, Any}

```

`grid`の緯度方向および経度方向の勾配。スペクトル空間に変換し、勾配の1/coslatスケーリングを解除します。単位球体上で作用し、`radius`キーワード引数が提供されない限り1/radiusスケーリングを省略します。既存のスペクトル変換`S`を利用します。
