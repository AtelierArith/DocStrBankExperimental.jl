```
MXH(
pr::AbstractVector{<:Real},
pz::AbstractVector{<:Real},
MXH_modes::Integer=5;
optimize_fit=false,
spline=false,
rmin=0.0,
rmax=0.0,
zmin=0.0,
zmax=0.0)
```

Compute Fourier coefficients for Miller-extended-harmonic representation:

```
R(θ) = R0 + R0*ϵ*cos(θᵣ(θ)) where θᵣ(θ) = θ + c0 + sum[c[m]*cos(m*θ) + s[m]*sin(m*θ)]
Z(θ) = Z0 - κ*R0*ϵ*sin(θ)
```

Where pr,pz are the flux surface coordinates and MXH*modes is the number of modes. `optimize*fit`keyword indicates to optimize the fit parameters to best go through the points`spline`keyword indicates to use spline integration for modes`rmin`,`rmax`,`zmin`,`zmax` force certain maximum and minimum values for the fit
