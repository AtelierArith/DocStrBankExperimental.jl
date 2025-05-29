```
SoftmaxPolicy <: ExplorationPolicy
```

は、ソフトマックス関数に従ってランダムなアクションをサンプリングするソフトマックスポリシーを表します。ソフトマックス関数は、オンポリシーのアクション値をサンプリングに使用される確率に変換します。温度パラメータまたは関数を使用して、結果の分布を広くしたり狭くしたりすることができます。

# コンストラクタ

`SoftmaxPolicy(problem, temperature::Union{Function, Float64}; rng=Random.default_rng())`

温度に関数が渡された場合、`temperature(k)`が呼び出され、`action(exploration_policy, on_policy, k, s)`を呼び出す際の温度の値が計算されます。

# フィールド

  * `temperature::Function`
  * `rng::AbstractRNG`
  * `actions::A` インデックス可能なアクションのリスト
