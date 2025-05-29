```
SpectralKernelOperator(transform, channels, σ = identity; init = glorot_uniform)
```

スペクトル変換 `trafo`、チャネル `channels`、活性化関数 `σ`、および初期化関数 `init` を持つスペクトルカーネルオペレーターを構築します。

参考文献: パラメトリック偏微分方程式のためのフーリエニューラルオペレーター - https://arxiv.org/abs/2010.08895

# 例

```
julia> trafo = FourierTransform(modes = (12, 3, 4, 12))
julia> channels = 1 => 4
julia> σ = relu
julia> conv = SpectralKernelOperator(trafo, channels, σ)
```
