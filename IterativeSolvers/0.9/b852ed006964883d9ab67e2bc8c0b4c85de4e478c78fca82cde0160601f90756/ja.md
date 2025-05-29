```
invpowm(B; shift = σ, kwargs...) -> λ, x, [history]
```

`shift`の近くにある行列$A$の近似固有対`(λ, x)`を見つけます。ここで、`B`は`B * v = inv(A - σI) * v`という効果を持つ線形写像です。

このメソッドは、`x0`がランダムな複素単位ベクトルである`powm!(B, x0; inverse = true, shift = σ)`を呼び出します。詳細は[`powm!`](@ref)を参照してください。

# 例

```julia
using LinearMaps
σ = 1.0 + 1.3im
A = rand(ComplexF64, 50, 50)
F = lu(A - σ * I)
Fmap = LinearMap{ComplexF64}((y, x) -> ldiv!(y, F, x), 50, ismutating = true)
λ, x = invpowm(Fmap, shift = σ, tol = 1e-4, maxiter = 200)
```
