```
fundamental_matrix(x)
```

# 定義

マルコフ連鎖の基本行列は、$C$が一時的状態から一時的状態への遷移行列であるとき、$(I-C)^{-1}$として定義されます。

基本行列の$(i, j)$番目の要素は、連鎖が状態$i$から始まったときに、全体のプロセスにおいて連鎖が状態$j$にいる期待回数です。

# 引数

  * `x`: 何らかのマルコフ連鎖。

# 戻り値

マルコフ連鎖の基本行列。

# 注意事項

`x`はすでに標準形であることが推奨されます。これは、配列出力の各要素を構成する状態が何であるかの混乱を避けるためです。

# 例

基本行列の典型的な例を示します。

```jldoctest fundamental_matrix
using DiscreteMarkovChains
T = [
    1.0 0.0 0.0;
    0.0 0.4 0.6;
    0.2 0.2 0.6;
]
X = DiscreteMarkovChain(T)

fundamental_matrix(X)

# 出力

2×2 Array{Float64,2}:
 3.33333  5.0
 1.66667  5.0
```

連鎖がエルゴード的である場合、基本行列は0x0行列です（一時的状態が存在しないため）。

```jldoctest fundamental_matrix
T = [
    0.0 1.0 0.0;
    0.5 0.0 0.5;
    0.0 1.0 0.0;
]
X = DiscreteMarkovChain(T)

fundamental_matrix(X)

# 出力

0×0 Array{Any,2}
```
