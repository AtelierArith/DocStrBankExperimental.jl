```
stationary_distribution(x)
```

# 定義

マルコフ連鎖の定常分布は、時間が進むにつれてマルコフ連鎖内で変わらない確率分布です。これは、要素の合計が1になる行ベクトル $w$ であり、$wT = w$ を満たします。$T$ はマルコフ連鎖の1ステップ遷移行列です。

言い換えれば、$w$ は行列 $T$ によって不変です。

簡単のために、この関数は行ベクトルの代わりに列ベクトルを返します。

連続マルコフ連鎖の場合、定常分布は $wQ = 0$ の解として与えられ、ここで $Q$ は遷移強度行列です。

# 引数

  * `x`: 何らかのマルコフ連鎖。

# 戻り値

方程式 $w'T = w'$ を満たす列ベクトル $w$。

# 例

定常分布は常に存在します。ただし、ユニークでない場合もあります。

ユニークであれば問題はありません。

```jldoctest stationary_distribution
using DiscreteMarkovChains
T = [
    4 2 4;
    1 0 9;
    3 5 2;
]//10
X = DiscreteMarkovChain(T)

stationary_distribution(X)

# 出力

3-element Array{Rational{Int64},1}:
 35//129
 12//43
 58//129
```

無限の解がある場合、原則解が取られます（すべての自由変数は0に設定されます）。ムーア・ペンローズの逆行列が使用されます。

```jldoctest stationary_distribution
T = [
    0.4 0.6 0.0;
    0.6 0.4 0.0;
    0.0 0.0 1.0;
]
X = DiscreteMarkovChain(T)

stationary_distribution(X)

# 出力

3-element Array{Float64,1}:
 0.33333333333333337
 0.33333333333333337
 0.33333333333333337
```

# 参考文献

1. [Brilliant.org](https://brilliant.org/wiki/stationary-distributions/#:~:text=A%20stationary%20distribution%20of%20a,transition%20matrix%20P%2C%20it%20satisfies)
