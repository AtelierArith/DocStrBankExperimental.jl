```julia
struct GaussianKineticEnergy{T<:(AbstractMatrix), S<:(AbstractMatrix)} <: DynamicHMC.EuclideanKineticEnergy
```

ガウス運動エネルギーは、$K(q,p) = p ∣ q ∼ 1/2 pᵀ⋅M⁻¹⋅p + log|M|$（定数なし）であり、$q$には依存しません。

逆共分散$M⁻¹$が保存されます。

!!! note
    $$
    M⁻¹
    $$

    を事後分散に近似させることは、合理的な出発点です。

