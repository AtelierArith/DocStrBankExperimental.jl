```
SpectralCovariance(transform, rank, channels; init = glorot_uniform)
```

スペクトル変換 `trafo`、低ランク行列ランク `rank`、チャネル `channels`、および初期化関数 `init` を持つスペクトル共分散演算子を構築します。

# 例

```
julia> trafo = FourierTransform(modes = (12, 3, 4, 12))
julia> channels = 1 => 4
julia> rank = 3
julia> conv = SpectralCovariance(trafo, rank, channels)
```
