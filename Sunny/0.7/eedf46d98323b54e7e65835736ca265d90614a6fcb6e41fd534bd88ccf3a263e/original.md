```
Units(energy, length)
```

Physical constants in units of reference `energy` and `length` scales. Possible lengths are `[:angstrom, :nm]`. For atomic scale modeling, it is preferable to work in units of `length=:angstrom`, which follows the CIF file standard. Possible energy units are `[:meV, :K, :THz, :inverse_cm, :T]`. Kelvin is converted to energy via the Boltzmann constant $k_B$. Similarly, hertz is converted via the Planck constant $h$, inverse cm via the speed of light $c$, and tesla (field strength) via the Bohr magneton $μ_B$. For a given `Units` system, one can access any of the length and energy scale symbols listed above.

# Examples

```julia
# Unit system with [energy] = meV and [length] = Å
units = Units(:meV, :angstrom)

# Use the Boltzmann constant kB to convert 1 kelvin into meV
@assert units.K ≈ 0.0861733326

# Use the Planck constant h to convert 1 THz into meV
@assert units.THz ≈ 4.135667696

# Use the constant h c to convert 1 cm⁻¹ into meV
@assert units.inverse_cm ≈ 0.1239841984

# Use the Bohr magneton μB to convert 1 tesla into meV
@assert units.T ≈ 0.05788381806

# The physical constant μ0 μB² in units of Å³ meV.
@assert u.vacuum_permeability ≈ 0.6745817653
```
