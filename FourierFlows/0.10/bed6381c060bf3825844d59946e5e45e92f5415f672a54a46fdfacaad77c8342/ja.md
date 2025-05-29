```
struct ETDRK4TimeStepper{T,TL} <: AbstractTimeStepper{T}
```

時間ステッピング `∂u/∂t = L * u + N(u)` のための4次指数時間差分ルンゲクッタタイムステッパーです。このスキームは線形項 `L` を正確に扱い、非線形項 `N(u)` には4次ルンゲクッタスキーム（[`RK4TimeStepper`](@ref)）を使用します。すなわち、

```julia
uⁿ⁺¹ = exp(L * dt) * uⁿ + RK4(N(uⁿ))
```

詳細については [Kassam-Trefethen-2005](@citet) を参照してください。
