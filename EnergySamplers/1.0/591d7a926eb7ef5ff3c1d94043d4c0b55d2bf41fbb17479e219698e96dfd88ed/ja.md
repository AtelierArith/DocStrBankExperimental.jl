```
(sampler::AbstractSampler)(
    model,
    rule::AbstractSamplingRule;
    niter::Int = 100,
    clip_grads::Union{Nothing,AbstractFloat} = 1e-2,
    n_samples::Union{Nothing,Int} = nothing,
    kwargs...,
)
```

`AbstractSampler`のためのサンプリングメソッド。このメソッドは、モデルの学習した分布からサンプルを生成します。

# 引数

  * `sampler::AbstractSampler`: 使用するサンプラー。
  * `model`: サンプリングするモデル。
  * `rule::AbstractSamplingRule`: 使用するサンプリングルール。
  * `niter::Int=100`: 実行する反復回数。
  * `clip_grads::Union{Nothing,AbstractFloat}=nothing`: 勾配をクリップするための値。この値は、結合エネルギーモデルのトレーニング時に勾配の爆発を防ぐのに役立ちます。`nothing`の場合、クリッピングは行われません。
  * `n_samples::Union{Nothing,Int}=nothing`: 生成するサンプルの数。
  * `kwargs...`: 追加のキーワード引数。

# 戻り値

  * `input_samples`: サンプラーによって生成されたサンプル。
