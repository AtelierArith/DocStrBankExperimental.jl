```
periodicities(x::AbstractDiscreteMarkovChain)
```

離散マルコフ連鎖のために設計された `communication_classes` のより高度なバージョンです。これは `communication_classes` と同じですが、周期性も返します。

# 定義

状態 $i$ の周期 $d_i$ は、$p^{(n)}_{i,i} > 0$ となるすべての整数 $n ∈ \mathbb{N}$ の最大公約数です。より簡潔に書くと、

$$
d_i = \text{gcd}\{ n ∈ \mathbb{N} | p^{(n)}_{i,i} > 0 \}
$$

もし $d_i=1$ であれば、状態 $i$ は非周期的であると言います。

# 引数

  * `x`: 何らかの種類の離散マルコフ連鎖。

# 戻り値

3つの配列を含むタプル。

  * 最初の配列は、通信する状態を格納するC配列を含みます。
  * 2番目の配列はBoolの配列で、i番目の値が真であればi番目の通信クラスは再帰的です。
  * 3番目の配列は各通信クラスの周期性です。

# 例

```jldoctest periodicities
using DiscreteMarkovChains
T = [
    1 0;
    0 1;
]
X = DiscreteMarkovChain(T)

periodicities(X)

# 出力

([[1], [2]], Any[true, true], Any[1, 1])
```

したがって、マルコフ連鎖には2つの通信クラスがあり、どちらも再帰的で非周期的です。

```jldoctest periodicities
T = [
    0.0 1.0 0.0;
    1.0 0.0 0.0;
    0.1 0.2 0.7;
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)

periodicities(X)

# 出力

([["Sunny", "Cloudy"], ["Rainy"]], Any[true, false], Any[2, 1])
```

したがって、Sunny と Cloudy の状態は通信し、周期2で再帰的です。Rainy の状態は一時的で非周期的です。これは、雨が止んだ後は二度と雨が降らないため、あまり良い天気モデルではないことに注意してください。また、その後の各日は、Sunny と Cloudy の間で振動します。
