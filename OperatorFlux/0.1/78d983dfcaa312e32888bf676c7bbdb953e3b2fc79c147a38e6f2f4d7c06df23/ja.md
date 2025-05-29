```
SpectralConv(transform, channels; init = glorot_uniform)
```

スペクトル変換 `trafo`、チャネル `channels`、および初期化関数 `init` を持つスペクトル畳み込み演算子を構築します。

# 例

```
julia> trafo = FourierTransform(modes = (12, 3, 4, 12))
julia> channels = 1 => 4
julia> conv = SpectralConv(trafo, channels)
```
