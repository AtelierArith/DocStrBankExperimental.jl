```
const PhysicalConstants
```

A `NamedTuple` which stores some constant values listed in [*CODATA recommended values of the fundamental physical constants: 2022*](https://physics.nist.gov/cuu/pdf/wall_2022.pdf)

The current stored constants are:

  * `c` : (exact) speed of light in vacuum with unit $[\textrm{m}\cdot\textrm{s}^{-1}]$
  * `G` : Newtonian constant of gravitation with unit $[\textrm{m}^3\cdot\textrm{kg}^{−1}\cdot\textrm{s}^{−2}]$
  * `h` : (exact) Planck constant with unit $[\textrm{J}\cdot\textrm{s}]$
  * `ħ` : reduced Planck constant with unit $[\textrm{J}\cdot\textrm{s}]$
  * `e` : (exact) elementary charge with unit $[\textrm{C}]$
  * `μ0` : vacuum magnetic permeability with unit $[\textrm{N}\cdot\textrm{A}^{-2}]$
  * `ϵ0` : vacuum electric permittivity with unit $[\textrm{F}\cdot\textrm{m}^{-1}]$
  * `k` : (exact) Boltzmann constant with unit $[\textrm{J}\cdot\textrm{K}^{-1}]$
  * `NA` : (exact) Avogadro constant with unit $[\textrm{mol}^{-1}]$

# Examples

```jldoctest
julia> PhysicalConstants.ħ
1.0545718176461565e-34
```
