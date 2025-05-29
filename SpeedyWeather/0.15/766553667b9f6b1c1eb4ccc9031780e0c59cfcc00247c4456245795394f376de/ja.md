```julia
initialize!(
    diffusion::SpeedyWeather.HyperDiffusion,
    model::SpeedyWeather.AbstractModel
)

```

`diffusion`内のハイパーディフュージョン項をモデルの時間ステップに基づいて事前計算し、垂直方向の強度/パワーが変化する可能性があります。
