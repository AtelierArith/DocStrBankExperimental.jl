```
DemoSystems
```

A module with standard test systems from the control literature.

The returned systems are of type `StateSpace` or `DelayLTISystem`.

Default parameter can be changed using keyword arguments.

# SISO systems

  * `DemoSystems.lag(;T=1)`     First-order system  `1/(sT+1)`
  * `DemoSystems.fotd(;T=1, τ=1)`   First-order system with time delay `exp(-sτ)/(sT+1)`
  * `DemoSystems.sotd(;T=1, T2=10, τ=1)`   Second-order non-resonant system with time delay `exp(-sτ)/(sT+1)/(sT2 + 1)`
  * `DemoSystems.resonant(;ω0=1, ζ=0.25)`   Second-order resonant systems `ω0^2/(s^2 + 2ζ*ω0*s + ω0^2)`
  * `DemoSystems.double_mass_model` Fourth-order model of a flexible transmission. See docstrings for details.

# MIMO systems

  * `DemoSystems.woodberry()`     Wood–Berry distillation column
  * `DemoSystems.doylesat(;a=10)`    The spinning body example by Doyle

Fore more information, see the help for the specific systems.
