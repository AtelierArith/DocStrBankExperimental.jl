```julia
mutable struct GaussianKineticEnergy{T<:(AbstractMatrix), S<:(AbstractMatrix)} <: BaytesMCMC.EuclideanKineticEnergy
```

ガウス運動エネルギーは、`q`に依存しません。

# フィールド

  * `Σ::AbstractMatrix`: 逆質量行列 Σ ~ 事後共分散行列
  * `Mᶜʰᵒˡ::AbstractMatrix`: 質量行列 M のコレスキー分解、すなわち Mᶜʰᵒˡ*Mᶜʰᵒˡ'=M。ランダムサンプルを生成するために使用されます。
