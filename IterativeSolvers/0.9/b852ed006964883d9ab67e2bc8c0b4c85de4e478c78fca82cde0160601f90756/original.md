```
invpowm(B; shift = σ, kwargs...) -> λ, x, [history]
```

Find the approximate eigenpair `(λ, x)` of $A$ near `shift`, where `B` is a linear map that has the effect `B * v = inv(A - σI) * v`.

The method calls `powm!(B, x0; inverse = true, shift = σ)` with `x0` a random, complex unit vector. See [`powm!`](@ref)

# Examples

```julia
using LinearMaps
σ = 1.0 + 1.3im
A = rand(ComplexF64, 50, 50)
F = lu(A - σ * I)
Fmap = LinearMap{ComplexF64}((y, x) -> ldiv!(y, F, x), 50, ismutating = true)
λ, x = invpowm(Fmap, shift = σ, tol = 1e-4, maxiter = 200)
```
