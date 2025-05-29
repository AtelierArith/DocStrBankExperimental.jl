```julia
struct TreeBelief{T<:DistributedFactorGraphs.InferenceVariable, P, M<:ManifoldsBase.AbstractManifold}
```

リファクタリング中の中間データ構造。

単一変数の信念の表現。

ノート：

  * ジョイントを送信したいので、これはまず統合 #459 を解決するためのものです。
  * 長期的な目標は単一のジョイント定義であり、おそらく `LikelihoodMessage` と呼ばれるでしょう。
