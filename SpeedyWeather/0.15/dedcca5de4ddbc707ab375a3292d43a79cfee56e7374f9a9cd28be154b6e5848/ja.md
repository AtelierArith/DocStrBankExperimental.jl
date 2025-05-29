```julia
initialize!(
    diffusion::SpeedyWeather.HyperDiffusion,
    G::SpeedyWeather.AbstractGeometry,
    L::SpeedyWeather.AbstractTimeStepper
)

```

モデルの時間ステップ `L` と垂直レベルのシグマレベル `G` に基づいて、すべての層のハイパーディフュージョン項を事前計算します。
