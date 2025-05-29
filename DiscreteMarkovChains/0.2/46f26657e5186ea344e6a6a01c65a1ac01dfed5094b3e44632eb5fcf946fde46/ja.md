```
decompose(x)
```

すべての遷移行列は、次のように再配置できます。

$$
T = \begin{pmatrix}
A & 0\\
B & C
\end{pmatrix}
$$

ここで、$A$、$B$、および $C$ は以下に説明されている通りです。$0$ はゼロの行列です。

# 引数

  * `x`: ある種のマルコフ連鎖。

# 戻り値

4つの値のタプル

  * `states`: 最初の値は新しい状態の配列です。
  * `A`: 2番目の値は再帰的状態から再帰的状態への行列です。
  * `B`: 3番目の値は一時的状態から再帰的状態への行列です。
  * `C`: 4番目の値は一時的状態から一時的状態への行列です。

# 例

```jldoctest decompose
using DiscreteMarkovChains
T = [
    0.0 1.0 0.0;
    1.0 0.0 0.0;
    0.1 0.2 0.7;
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)

decompose(X)

# output

(Any["Sunny", "Cloudy", "Rainy"], [0.0 1.0; 1.0 0.0], [0.1 0.2], [0.7])
```
