```
struct VerticallyImplicitTimeDiscretization <: AbstractTimeDiscretization
```

`TurbulenceClosure`の垂直的暗黙時間離散化。

これは、$n$-番目のタイムステップでのフラックスダイバージェンス$𝛁 ⋅ 𝐪$が次のように時間離散化されることを意味します。

```julia
[∇ ⋅ q]ⁿ = [explicit_flux_divergence]ⁿ + [∂z (κ ∂z c)]ⁿ⁺¹
```
