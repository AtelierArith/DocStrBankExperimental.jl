```
function TrainingStats(;
    retcode::Union{String, Nothing} = nothing,
    losses::Vector{F} = Float64[],
    niter::I = 0
) where {F <: AbstractFloat, I <: Int}
```

TrainingStatsオブジェクトのコンストラクタで、トレーニング中の重要な情報を保存するために使用されます。

# 引数

  * `retcode`: 最適化の報告コード。
  * `losses`: 各イテレーションでの損失関数の値を格納するベクター。
  * `niter`: 総イテレーション数/エポック数。
  * `θ`: トレーニング後のニューラルネットワークのパラメータ。
