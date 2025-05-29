```
MXH(R0::T, Z0::T, ϵ::T, κ::T, c0::T, c::U, s::U) where {T<:Real,U<:AbstractVector{<:Real}}
```

Return MXH for Miller-extended-harmonic representation:

```
R(θ) = R0 + R0*ϵ*cos(θᵣ(θ)) where θᵣ(θ) = θ + c0 + sum[c[m]*cos(m*θ) + s[m]*sin(m*θ)]
Z(θ) = Z0 - κ*R0*ϵ*sin(θ)
```
