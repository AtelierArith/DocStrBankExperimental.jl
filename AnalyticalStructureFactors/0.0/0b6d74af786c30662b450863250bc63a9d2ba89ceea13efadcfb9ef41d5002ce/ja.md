```
S_HS_PY(ϕ::T, k::T) where {T<:AbstractFloat}
```

ハードスフェアのための静的構造因子 S(k) を Percus-Yevick (PY) クロージャーの下で返します。入力 `k` は無次元波ベクトル k = q*sigma であることが期待されます。

使用される式は次のとおりです: S(k) = 1 / (1 - 24*ϕ*c(k))

# 引数

  * `ϕ::T`: 体積分率。範囲は `[0, 1)` である必要があります。
  * `k::T`: 無次元波ベクトル、k = q*sigma。

# 戻り値

  * 静的構造因子 S(k) の値。

# 参考文献

[1] J. P. Hansen and I. McDonald. Theory of Simple Liquids. Academic, London, 1990. ```
