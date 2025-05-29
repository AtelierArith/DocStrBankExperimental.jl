```
scalar_normalizer(;weights = OnlineStats.EqualWeight())
```

スカラーのトレース（報酬など）用に事前設定されたノーマライザーを返します。デフォルトでは、すべてのサンプルはモーメントの計算において等しい重みを持ちます。最近の観測を重視するために指数重みなどのバリアントを使用するには、[OnlineStatsのドキュメント](https://joshday.github.io/OnlineStats.jl/stable/weights/)を参照してください。
