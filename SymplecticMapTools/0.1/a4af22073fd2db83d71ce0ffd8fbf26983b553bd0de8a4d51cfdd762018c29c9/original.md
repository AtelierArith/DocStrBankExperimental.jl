```
get_circle_residual(F::Function, z::InvariantCircle, Nθ::Integer)
```

Get the KAM-like residual of a chain of p invariant circles.
>   Rᵢ₁ = z₁(θᵢ+τ) - F(z_p(θᵢ))
>   Rᵢⱼ = zⱼ(θᵢ) - F(zⱼ₋₁(θᵢ)) for 2<=j<=p

Arguments:

  * `F`: Symplectic map
  * `z`: Invariant circle
  * `Nθ`: Number of θ points where the residual is taken
