```
OptimizeParameters(kind=MinRecall(0.9);
    initialpopulation=16,
    maxiters=12,
    bsize=4,
    ksearch=10,
    queries=nothing,
    numqueries=32,
    verbose=false,
    params=SearchParams(; maxpopulation=initialpopulation, bsize, mutbsize=4bsize, crossbsize=2bsize, maxiters, verbose),
    space::BeamSearchSpace=BeamSearchSpace()
)
```

与えられたパラメータを使用してハイパー最適化コールバックを作成します

# 引数

  * `kind`: エラーファンクションの種類、例: `MinRecall(0.9)`。
  * `hints`: 検索ヒントがどのように計算されるべきか。
  * `initialpopulation`: 初期の構成数を決定する最適化引数。
  * `maxiters`: イテレーションの数を決定する最適化引数。
  * `bsize`: どれだけの上位構成が変異および交差できるかを決定する最適化引数。
  * `params`: `SearchParams` 引数（別々の最適化引数が不十分な場合）
  * `ksearch`: 最適化プロセスによって取得される隣接数。
  * `queries`: 最適化プロセス中に使用されるクエリセット。
  * `numqueries`: 最適化プロセス中に実行されるクエリの数。
  * `space`: 構成検索空間

# 詳細を見る

  * [`BeamSearchSpace`](@ref)を参照してください
  * [`SearchParams` arguments of `SearchModels.jl`](https://github.com/sadit/SearchModels.jl)

詳細については
