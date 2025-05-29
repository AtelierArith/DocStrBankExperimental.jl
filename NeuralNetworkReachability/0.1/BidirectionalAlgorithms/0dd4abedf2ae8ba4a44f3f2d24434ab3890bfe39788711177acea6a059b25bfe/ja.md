```
SimpleBidirectional{FA<:ForwardAlgorithm, BA<:BackwardAlgorithm} <: BidirectionalAlgorithm
```

単純な双方向アルゴリズムで、前方アルゴリズムと後方アルゴリズムにパラメトリックです。

### フィールド

  * `fwd_algo` – 前方アルゴリズム
  * `bwd_algo` – 後方アルゴリズム
