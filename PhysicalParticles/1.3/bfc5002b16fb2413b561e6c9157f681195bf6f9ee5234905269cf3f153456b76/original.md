```julia
Constant(; ...) -> PhysicalParticles.Constant
Constant(
    units;
    c_0,
    G,
    h,
    e,
    m_e,
    m_n,
    m_p,
    σ,
    H,
    k_B,
    ε_0,
    μ_0,
    ACC0
) -> PhysicalParticles.Constant

```

Construct an immutable struct storing basic physical constants corresponding to `units` (default is `uAstro`).

## Keywords

  * c:    Speed of light
  * G:    Newtonian constant of gravitation
  * m_e:  Electron mass
  * m_n:  Neutron mass
  * m_p:  Protron mass
  * k_B:  Kelvin-Boltzmann constant
  * ACC0: Modified gravitational acceleration constant

## Examples

```jl
Constant()
Constant(uSI)
Constant(uCGS)
using Unitful
ustrip(Constant())
```
