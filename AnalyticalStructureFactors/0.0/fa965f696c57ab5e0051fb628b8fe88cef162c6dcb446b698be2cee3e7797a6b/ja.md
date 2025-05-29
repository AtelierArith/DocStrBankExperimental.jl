```
k_VW(ϕ_HS::T, k_HS::T) where {T<:AbstractFloat}
```

ハードスフェアのための波ベクトル補正をVerlet-Weiss (VW)近似を用いて計算します。これにより、効果的な波ベクトル k*eff が得られます。k*eff = k*HS * (ϕ*eff / ϕ_HS)^(1/3)

# 引数

  * `ϕ_HS::T`: ハードスフェア系の元の充填率。
  * `k_HS::T`: 元の（無次元の）波ベクトル。

# 戻り値

  * `T`: Verlet-Weiss 補正された効果的な波ベクトル。

# 参考文献

[1] Loup Verlet and Jean-Jacques Weis. Phys. Rev. A 5, 939 – Published 1 February 1972.
