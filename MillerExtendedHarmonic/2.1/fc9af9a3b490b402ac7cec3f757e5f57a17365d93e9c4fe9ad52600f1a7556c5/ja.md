```
MXH(R0::Real, Z0::Real, ϵ::Real, κ::Real, c0::Real, c::AbstractVector{<:Real}, s::AbstractVector{<:Real})
```

Miller-拡張ハーモニック表現のためのMXHを返します：

```
R(θ) = R0 + R0*ϵ*cos(θᵣ(θ)) ただし θᵣ(θ) = θ + c0 + sum[c[m]*cos(m*θ) + s[m]*sin(m*θ)]
Z(θ) = Z0 - κ*R0*ϵ*sin(θ)
```
