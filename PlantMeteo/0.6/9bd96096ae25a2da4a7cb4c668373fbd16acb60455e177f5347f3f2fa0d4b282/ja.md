```
psychrometer_constant(P, λ, Cₚ, ε; check=true)
psychrometer_constant(P, λ; check=true)
```

γ、湿度計定数は、湿度定数とも呼ばれます (kPa K−1)。MonteithとUnsworth (2013)、p. 222を参照してください。

# 引数

  * `P` (kPa): 気圧
  * `λ` ($J\ kg^{-1}$): 水の蒸発潜熱 (see [`latent_heat_vaporization`](@ref))
  * `Cₚ` (J kg-1 K-1): 定圧での空気の比熱 ($J\ K^{-1}\ kg^{-1}$)
  * `ε` (摂氏度): 0ケルビンでの摂氏度
  * `check` (Bool): Pが85-110 kPaの地球範囲内にあるかどうかを確認

# 注意

Cₚ、εおよびλ₀は、提供されていない場合は[`Constants`](@ref)から取得されます。

```julia
Tₐ = 20.0

λ = latent_heat_vaporization(Tₐ, λ₀)
psychrometer_constant(100.0, λ)
```

# 参考文献

Monteith, John L., et Mike H. Unsworth. 2013. « Chapter 13 - Steady-State Heat Balance: (i) Water Surfaces, Soil, and Vegetation ». In Principles of Environmental Physics (Fourth Edition), edited by John L. Monteith et Mike H. Unsworth, 217‑47. Boston: Academic Press.
