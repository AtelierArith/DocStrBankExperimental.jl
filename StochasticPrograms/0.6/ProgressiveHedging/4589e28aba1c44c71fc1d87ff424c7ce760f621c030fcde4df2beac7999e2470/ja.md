```
ProgressiveHedgingAlgorithm
```

プログレッシブヘッジングアルゴリズムのファンクタオブジェクト。`ProgressiveHedgingSolver`ファクトリ関数を使用して作成し、その後`StochasticPrograms.jl`モデルに渡します。

...

# パラメータ

  * `τ::AbstractFloat = 1e-6`: 収束チェックのための相対許容誤差。
  * `log::Bool = true`: プログレッシブヘッジング手順を標準出力にログするかどうかを指定します。

...
