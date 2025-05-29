```
C_HS_PY(ϕ::T, k::T) where {T<:AbstractFloat}
```

ハードスフェアのためのPercus-Yevick (PY)近似を使用して、無次元の直接相関関数c(k*sigma)を計算します。結果はc(q*sigma)であり、qは波ベクトルの大きさ、sigmaは粒子の直径です。入力`k`は無次元波ベクトルk = q*sigmaであることが期待されます。

# 引数

  * `ϕ::T`: 球の体積分率。範囲は`[0, 1)`である必要があります。
  * `k::T`: 無次元波ベクトル、k = q*sigma、ここでqは波ベクトル、sigmaは球の直径です。

# 戻り値

  * 直接相関関数c(k)の値。

# 参考文献

[1] J. P. Hansen and I. McDonald. Theory of Simple Liquids. Academic, London, 1990.
