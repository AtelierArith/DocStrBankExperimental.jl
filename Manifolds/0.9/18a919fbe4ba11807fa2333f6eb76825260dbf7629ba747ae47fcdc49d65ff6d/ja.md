```
project(::Flag, p, X)
```

ベクトル `X` を [`Flag`](@ref) 多様体の点 `p` での接空間に射影します。式は [YeWongLim:2021](@cite) に従います：

$$
Y_i = X_i - (p_i p_i^{\mathrm{T}}) X_i + \sum_{j \neq i} p_j X_j^{\mathrm{T}} p_i
$$

ここで $i$ は 1 から $d$ までで、結果のベクトルは $Y = [Y_1, Y_2, …, Y_d]$ であり、$X = [X_1, X_2, …, X_d]$、$p = [p_1, p_2, …, p_d]$ はフラグの連続する部分空間の基底ベクトル行列への分解です。
