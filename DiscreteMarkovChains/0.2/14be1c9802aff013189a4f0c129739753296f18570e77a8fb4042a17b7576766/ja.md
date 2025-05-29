```
is_regular(x)
```

# 定義

マルコフ連鎖は、遷移行列のあるべき冪がすべて正の要素を持つ場合、正則連鎖と呼ばれます。これは、エルゴード性と非周期性であることと同等です。

# 引数

  * `x`: 何らかの種類の離散マルコフ連鎖。

# 戻り値

マルコフ連鎖 `x` が正則であれば `true` を返します。

# 例

2つの通信クラスを持つ行列を設定し、それが正則でないことを示します。

```jldoctest is_regular
using DiscreteMarkovChains
T = [
    0 1 0;
    1 0 0;
    0 0 1;
]
X = DiscreteMarkovChain(T)

is_regular(X)

# 出力

false
```

上記を繰り返しますが、今度はすべての状態が通信します。

```jldoctest is_regular
T = [
    0.0 0.5 0.5;
    0.0 0.0 1.0;
    1.0 0.0 0.0;
]
X = DiscreteMarkovChain(T)

is_regular(X)

# 出力

true
```

周期的な連鎖が正則でないことに注意してください。通信クラスは1つだけです。

```jldoctest is_regular
T = [
    0 1 0;
    0 0 1;
    1 0 0;
]
X = DiscreteMarkovChain(T)

is_regular(X)

# 出力

false
```
