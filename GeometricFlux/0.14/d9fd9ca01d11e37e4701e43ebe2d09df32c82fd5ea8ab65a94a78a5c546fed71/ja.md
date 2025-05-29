```
ChebConv(in=>out, k; bias=true, init=glorot_uniform)
```

チェビシェフスペクトルグラフ畳み込み層。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `k`: チェビシェフ多項式の次数。
  * `bias`: 学習可能なバイアスを追加。
  * `init`: 重みの初期化方法。

# 例

```jldoctest
julia> cc = ChebConv(1024=>256, 5, relu)
ChebConv(1024 => 256, k=5, relu)
```

静的グラフでのトレーニング層については [`WithGraph`](@ref) を参照してください。
