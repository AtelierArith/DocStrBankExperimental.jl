```
NormalFormGame(payoffs)
```

N次元配列 `payoffs` のベクトルを持つ N プレイヤーの NormalFormGame を構築します。ここで、`payoffs[a_1, a_2, ..., a_N]` は、アクションプロファイル (a*1, a*2, ..., a_N) に対する各プレイヤーの N のペイオフ値を含むベクトルです。

# 引数

  * `payoffs::Array{AbstractVector{T<:Real}}` : ベクトルとしてのペイオフプロファイルを含む、次元数 N の配列。
