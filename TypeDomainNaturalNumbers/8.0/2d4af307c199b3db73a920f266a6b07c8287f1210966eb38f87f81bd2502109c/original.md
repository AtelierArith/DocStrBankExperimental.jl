```
IrrationalPowerMultiple
```

An improved `Irrational`. Supports exact arithmetic with [`TypeDomainRational`](@ref) and with `Irrational`, by storing a nonzero [`TypeDomainInteger`](@ref) exponent and a nonzero [`TypeDomainRational`](@ref) factor together with an `Irrational`.

The constructor converts from `Irrational`.

Supports some exact arithmetic, including with [`TypeDomainRational`](@ref), with [`TypeDomainNaturalLogarithm`](@ref) and with `Irrational`.

Has three type parameters:

  * the base
  * the exponent that the base is raised to
  * the factor that the rest is multiplied with

Even though it currently happens to be an abstract type, subtyping `IrrationalPowerMultiple` from outside this package is forbidden.
