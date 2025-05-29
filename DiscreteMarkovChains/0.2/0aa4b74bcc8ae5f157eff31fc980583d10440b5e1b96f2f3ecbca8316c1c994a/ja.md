```
canonical_form(x)
```

`x`の遷移行列の状態を再配置し、再帰状態が最初に、過渡状態が最後に表示されるようにします。

# 引数

  * `x`: 何らかのマルコフ連鎖。

# 戻り値

新しい状態と新しい遷移行列を含むタプル。

# 例

前の例と同じ行列を使用しますが、その順序を変更します。

```jldoctest canonical_form
using DiscreteMarkovChains
T = [
    0.7 0.2 0.1;
    0.0 0.0 1.0;
    0.0 1.0 0.0;
]
X = DiscreteMarkovChain(["Rainy", "Cloudy", "Sunny"], T)

canonical_form(X)

# 出力

(Any["Cloudy", "Sunny", "Rainy"], [0.0 1.0 0.0; 1.0 0.0 0.0; 0.2 0.1 0.7])
```

ここでは、CloudyとSunnyが再帰状態であるため、最初に表示されます。Rainyは過渡状態であるため、最後に表示されます。
