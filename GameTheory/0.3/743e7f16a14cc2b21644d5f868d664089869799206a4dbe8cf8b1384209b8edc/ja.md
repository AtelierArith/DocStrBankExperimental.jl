```
NormalFormGame(payoffs)
```

N人のNormalFormGameを構築します。N>=2で、M=N+1次元の配列`payoffs`を使用します。ここで、`payoffs[a_1, a_2, ..., a_N, :]`はNのペイオフ値のプロファイルを含みます。

# 引数

  * `payoffs::Array{T<:Real}` : ペイオフプロファイルを含むndims=N+1の配列。
