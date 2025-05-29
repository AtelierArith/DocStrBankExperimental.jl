```
mis_postprocessing(config, graph::AbstractGraph; ntrials::Int=10)
```

ハーバード実験でMISを見つけるために使用される後処理プロトコル: [arxiv:2202.09372](https://arxiv.org/abs/2202.09372)。これは、[`to_independent_set`](@ref) と [`add_random_vertices`](@ref) の組み合わせを含みます。

# 引数

  * `config`: 後処理のための設定。
  * `graph`: 問題のグラフ。

# キーワード引数

  * `ntrials`: 使用する試行の数。
