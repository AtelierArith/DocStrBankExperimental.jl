```
PCAEmbedding(s, em::AbstractSpatialEmbedding; kwargs...) → embedding
```

主成分分析を次元削減の手段として用いた時空間遅延座標構造であり、`embedding`はファンクタとして使用できます：

```julia
embedding(rvec, s, t, α)
```

これは`rvec`に対してインプレースで動作し、時刻`t`における空間時系列`s`からベクトルを再構成します。また、デカルトインデックス`α`を使用します。

この`embedding`をインスタンス化するには、再構成するデータ`s`と[`SpatioTemporalEmbedding`](@ref)のインスタンスを`PCAEmbedding`に渡します。

## キーワード引数

  * `pratio = 0.99` : 低次元PCA再構成で保持する必要がある分散の比率。
  * `maxoutdim = 25`: 出力次元の上限。`pratio`基準を破る可能性があります。
  * `every_t = 1` : 時間のn番目のポイントのみを使用することで計算を高速化します。
  * `every_α = 1` : 空間のn番目のポイントのみを使用することで計算をさらに高速化します（線形インデックス）。

出力次元を特定の値`X`に設定するには、`pratio=1, maxoutdim=X`を渡します。
