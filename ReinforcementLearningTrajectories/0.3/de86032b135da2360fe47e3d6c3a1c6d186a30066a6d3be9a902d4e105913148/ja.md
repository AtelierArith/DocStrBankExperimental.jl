```
array_normalizer(size::Tuple{Int}; weights = OnlineStats.EqualWeight())
```

配列トレース（ベクトルや行列の状態など）用に事前設定されたノーマライザーを返します。 `size` は状態の次元サイズを含むタプルです。例えば、10要素のベクトルの場合は `(10,)`、正方形の画像の場合は `(252,252)` です。デフォルトでは、すべてのサンプルはモーメントの計算において等しい重みを持ちます。最近の観測値を重視するために指数重みなどのバリアントを使用するには、[OnlineStats ドキュメント](https://joshday.github.io/OnlineStats.jl/stable/weights/) を参照してください。
