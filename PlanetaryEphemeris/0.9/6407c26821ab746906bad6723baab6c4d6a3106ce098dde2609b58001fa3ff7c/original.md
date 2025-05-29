```
pole_rotation(α::T, δ::T, W::T=zero(α)) where {T <: Number}
```

Return the rotation matrix from the inertial frame to the frame with pole at right ascension $\alpha$, declination $\delta$ and prime meridian at $W$

$$
A = R_z(W + \Delta W)R_x\left(\frac{\pi}{2} - \delta - \Delta\delta\right)R_z\left(\alpha + \Delta\alpha + \frac{\pi}{2}\right).
$$

See equation (6-3) in page 6-5 of https://doi.org/10.1002/0471728470.

$\textbf{Note:}$ Rotation matrices $(R_x, R_y, R_z)$ convention is the same as equations (11), (12) and (13) in page 9 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

See also [`Rx`](@ref) and [`Rz`](@ref).
