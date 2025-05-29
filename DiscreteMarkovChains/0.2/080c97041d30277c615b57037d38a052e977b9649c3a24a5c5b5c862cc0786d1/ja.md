```
DiscreteMarkovChain(transition_matrix)
DiscreteMarkovChain(state_space, transition_matrix)
DiscreteMarkovChain(continuous_markov_chain)
```

新しい離散マルコフ連鎖オブジェクトを作成します。

# 引数

  * `state_space`: マルコフ連鎖を構成する状態の名前。
  * `transition_matrix`: 単一ステップの遷移確率行列。
  * `continuous_markov_chain`: `ContinuousMarkovChain`のインスタンス。

# 例

以下は基本的な晴れ-曇り-雨の天気モデルを示しています。

```jldoctest DiscreteMarkovChain
using DiscreteMarkovChains
T = [
    0.9 0.1 0;
    0.5 0.2 0.3;
    0.1 0.4 0.5
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)
println(state_space(X))

# 出力

["Sunny", "Cloudy", "Rainy"]
```

```jldoctest DiscreteMarkovChain
println(transition_matrix(X))

# 出力

[0.9 0.1 0.0; 0.5 0.2 0.3; 0.1 0.4 0.5]
```

# 参考文献

1. [Wikipedia](https://en.wikipedia.org/wiki/Markov_chain#Discrete-time_Markov_chain)
2. [Dartmouth College](https://www.dartmouth.edu/~chance/teaching_aids/books_articles/probability_book/Chapter11.pdf)
