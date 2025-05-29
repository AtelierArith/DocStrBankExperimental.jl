```
ConstantCompressibilityDensities(
    sys_or_nph::Union{MultiPhaseSystem, Integer},
    reference_pressure = 1.0,
    reference_density = 0.0,
    compressibility = 1.0
)
```

Secondary variable that implements a constant compressibility relationship for density. Given the reference pressure, compressibility and density at the reference pressure, each phase density can be computed as:

$ρ(S) = ρ_{ref} e^{(p - p_{ref})c}$

The constructor can take in either one value per phase or a single value for all phases for the reference pressure, compressibility and density at reference conditions.

## Fields

  * `reference_pressure`: Reference pressure for each phase (where the reference densities are given)
  * `reference_densities`: Densities at the reference point
  * `compressibility`: Compressibility factor used when expanding around reference pressure, typically between 1e-3 and 1e-10
