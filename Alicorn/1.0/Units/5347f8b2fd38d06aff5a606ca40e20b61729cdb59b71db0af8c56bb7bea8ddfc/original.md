```
BaseUnit <: AbstractUnit
```

A named unit derived from the seven basic SI units.

# Fields

  * `name::String`: long form name of the unit
  * `symbol::String`: short symbol used to denote the named unit in a composite unit
  * `prefactor::Real`: numerical prefactor multiplying the polynomial of basic SI units corresponding to the named unit.
  * `exponents::BaseUnitExponents`: collection of the powers in the polynomial of basic SI units corresponding to the named unit.

# Constructor

```
BaseUnit(; name::String, symbol::String, prefactor::Real, exponents::BaseUnitExponents)
```

# Raises Exceptions

  * `Core.ArgumentError`: if attempting to initialize the `name` field with a string that is not valid as an identifier
  * `Core.DomainError`: if attempting to initialize the `prefactor` field with an infinite number

# Examples

1. The meter can be represented by

    ```jldoctest
    julia> BaseUnit( name="meter",
                     symbol="m",
                     prefactor=1,
                     exponents=BaseUnitExponents(m=1) )
    BaseUnit meter (1 m = 1 m)
    ```
2. The gram can be represented by

    ```jldoctest
    julia> BaseUnit( name="gram",
                     symbol="g",
                     prefactor=1e-3,
                     exponents=BaseUnitExponents(kg=1) )
    BaseUnit gram (1 g = 1e-3 kg)
    ```
3. The joule is defined as

    $$
    1\,\mathrm{J} = 1\,\mathrm{kg}\,\mathrm{m^2}\,\mathrm{s^{-2}}.
    $$

    and can be represents by

    ```jldoctest
    julia> BaseUnit( name="joule",
                     symbol="J",
                     prefactor=1,
                     exponents=BaseUnitExponents(kg=1, m=2, s=-2) )
    BaseUnit joule (1 J = 1 kg m^2 s^-2)
    ```
