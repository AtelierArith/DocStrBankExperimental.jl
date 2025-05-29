```
ContinuousMarkovChain(transition_matrix)
ContinuousMarkovChain(state_space, transition_matrix)
ContinuousMarkovChain(discrete_markov_chain)
```

新しい連続マルコフ連鎖オブジェクトを作成します。これはマルコフジャンププロセスとも呼ばれます。

不可約な有限連続時間マルコフ連鎖は常に正帰納的であり、その定常分布は常に存在し、ユニークであり、極限分布に等しいことに注意してください。

# 引数

  * `state_space`: マルコフ連鎖を構成する状態の名前。
  * `transition_matrix`: 遷移強度行列。生成行列とも呼ばれます。
  * `discrete_markov_chain`: `DiscreteMarkovChain`のインスタンス。

# 例

以下は基本的な晴れ-曇り-雨の天気モデルを示しています。

```jldoctest ContinuousMarkovChain
using DiscreteMarkovChains
T = [
    -.1 0.1 0.0;
    0.5 -.8 0.3;
    0.1 0.4 -.5;
]
X = ContinuousMarkovChain(["Sunny", "Cloudy", "Rainy"], T)
println(state_space(X))

# 出力

["Sunny", "Cloudy", "Rainy"]
```

```jldoctest ContinuousMarkovChain
println(transition_matrix(X))

# 出力

[-0.1 0.1 0.0; 0.5 -0.8 0.3; 0.1 0.4 -0.5]
```

# 参考文献

1. [Wikipedia](https://en.wikipedia.org/wiki/Continuous-time_Markov_chain)
