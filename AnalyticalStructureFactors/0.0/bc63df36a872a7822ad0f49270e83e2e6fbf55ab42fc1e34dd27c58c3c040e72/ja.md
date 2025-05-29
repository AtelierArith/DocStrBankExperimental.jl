```
phi_VW(ϕ_HS::T) where {T<:AbstractFloat}
```

ハードスフェアのための密度補正（有効充填率 ϕ*eff）をVerlet-Weiss (VW) 近似を使用して計算します。 ϕ*eff = ϕ*HS * (1 - ϕ*HS / 16)

# 引数

  * `ϕ_HS::T`: ハードスフェアシステムの充填率。

# 戻り値

  * `T`: Verlet-Weiss 補正された有効充填率。

# 参考文献

[1] Loup Verlet and Jean-Jacques Weis. Phys. Rev. A 5, 939 – Published 1 February 1972.
