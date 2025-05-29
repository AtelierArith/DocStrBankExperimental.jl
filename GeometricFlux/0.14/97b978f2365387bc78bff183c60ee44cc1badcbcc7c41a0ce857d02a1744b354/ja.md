```
GCNConv(in => out, σ=identity; bias=true, init=glorot_uniform)
```

グラフ畳み込み層。層への入力は、サイズが `(num_features, num_nodes)` のノード特徴配列 `X` です。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `σ`: 活性化関数。
  * `bias`: 学習可能なバイアスを追加。
  * `init`: 重みの初期化方法。

# 例

```jldoctest
julia> gc = GCNConv(1024=>256, relu)
GCNConv(1024 => 256, relu)
```

静的グラフでの層のトレーニングについては、[`WithGraph`](@ref)を参照してください。
