```
set_field!(sys::System, B_μB)
```

Sets the external magnetic field $𝐁$ scaled by the Bohr magneton $μ_B$. This scaled field has units of energy and couples directly to the dimensionless [`magnetic_moment`](@ref). At every site, the Zeeman coupling contributes an energy $+ (𝐁 μ_B) ⋅ (g 𝐒)$, involving the local $g$-tensor and spin angular momentum $𝐒$. Commonly, $g ≈ +2$ such that $𝐒$ is favored to anti-align with the applied field $𝐁$. Note that a given system of [`Units`](@ref) will implicitly use the Bohr magneton to convert between field and energy dimensions.

# Example

```julia
# In units of meV, apply a 2 tesla field in the z-direction
units = Units(:meV, :angstrom)
set_field!(sys, [0, 0, 2] * units.T)
```
