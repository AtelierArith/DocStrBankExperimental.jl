```
IS_HS_PY(ϕ::T, k::T) where {T<:AbstractFloat}
```

ハードスフェアの静的構造因子の逆数 1/S(k) を、Percus-Yevick (PY) 近似からの直接相関関数 c(k) を使用して計算します。逆構造因子は 1/S(k) = 1 - n * c*tilde(q) で与えられ、ここで n は数密度、c*tilde(q) は c(r) のフーリエ変換です。PYハードスフェアの場合、これはしばしば 1/S(k) = 1 - 24*ϕ*c*PY(k) と書かれ、c*PY(k) は `C_HS_PY` によって計算された無次元形式です。

# 引数

  * `ϕ::T`: 球の体積分率。範囲は `[0, 1)` である必要があります。
  * `k::T`: 無次元波ベクトル、k = q*sigma。

# 戻り値

  * 逆静的構造因子 1/S(k) の値。

# 参考文献

[1] J. P. Hansen and I. McDonald. Theory of Simple Liquids. Academic, London, 1990.
