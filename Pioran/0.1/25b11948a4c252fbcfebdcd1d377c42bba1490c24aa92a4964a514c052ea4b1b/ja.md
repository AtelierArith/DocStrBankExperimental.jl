スケーラブルなガウス過程は、半分可分カーネルから形成された共分散関数を持っています。

# 例

```julia
using Pioran
𝓟 = SingleBendingPowerLaw(1.0, 1.0, 2.0)
𝓡 = approx(𝓟, 1e-4, 1e-1, 30, 2.31,basis_function="SHO")
μ = 1.2

f = ScalableGP(𝓡) # ゼロ平均のGP
f = ScalableGP(μ, 𝓡) # 平均μを持つ
```

詳細については、[Foreman-Mackey et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..220F)を参照してください。
