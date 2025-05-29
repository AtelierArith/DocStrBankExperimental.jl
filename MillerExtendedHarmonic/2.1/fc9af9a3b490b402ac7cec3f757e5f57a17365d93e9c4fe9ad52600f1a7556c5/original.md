```
MXH(R0::Real, Z0::Real, ϵ::Real, κ::Real, c0::Real, c::AbstractVector{<:Real}, s::AbstractVector{<:Real})
```

Return MXH for Miller-extended-harmonic representation:

```
R(θ) = R0 + R0*ϵ*cos(θᵣ(θ)) where θᵣ(θ) = θ + c0 + sum[c[m]*cos(m*θ) + s[m]*sin(m*θ)]
Z(θ) = Z0 - κ*R0*ϵ*sin(θ)
```
