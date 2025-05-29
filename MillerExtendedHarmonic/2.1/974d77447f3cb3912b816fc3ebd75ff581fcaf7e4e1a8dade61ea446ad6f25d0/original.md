```
    MXH(pr::AbstractVector{<:Real}, pz::AbstractVector{<:Real}, R0::Real, Z0::Real, a::Real, b::Real, MXH_modes::Integer;
         optimize_fit=false, spline=false)
```

Compute Fourier coefficients for Miller-extended-harmonic representation:

```
R(θ) = R0 + R0*ϵ*cos(θᵣ(θ)) where θᵣ(θ) = θ + c0 + sum[c[m]*cos(m*θ) + s[m]*sin(m*θ)]
Z(θ) = Z0 - κ*R0*ϵ*sin(θ)
```

Where pr,pz are the flux surface coordinates and MXH*modes is the number of modes. `optimize*fit`keyword indicates to optimize the fit parameters to best go through the points`spline` keyword indicates to use spline integration for modes

N.B.: If `optimize_fit` is false, some MXH values are fixed, namely R0=R0, Z0=Z0, ϵ=a/R0, and κ=b/a       Otherwise, these are just the starting values for the optimzation
