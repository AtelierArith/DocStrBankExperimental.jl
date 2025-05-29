```julia
struct Jeckelmann <: MPSKit.DDMRG_Flavour
```

動的DMRGの元のフレーバーで、次の（2次の）コスト関数を最小化します：

$$
|| (H - E) |ψ₀⟩ - |ψ⟩ ||
$$

よりコストが低いが精度が低い代替手段については、[`NaiveInvert`](@ref)を参照してください。

## 参考文献

  * [Jeckelmann. Phys. Rev. B 66 (2002)](@cite jeckelmann2002)
