```
BaseUnitExponents
```

Collection of powers exponentiating each of the seven SI basic units.

The exponents $(a, b, c, d, e, f, g)$ are interpreted as the powers to which the seven SI basic units are raised:

$$
\mathrm{kg}^a \, \mathrm{m}^b \, \mathrm{s}^c \, \mathrm{A}^d \, \mathrm{K}^e \, \mathrm{mol}^f \, \mathrm{cd}^g.
$$

The [`BaseUnit`](@ref) type uses `BaseUnitExponents` to define named units in terms of the basic units.

# Fields

  * `kilogramExponent::Real`: power $a$ of kilogram
  * `meterExponent::Real`: power $b$ of meter
  * `secondExponent::Real`: power $c$ of second
  * `ampereExponent::Real`: power $d$ of ampere
  * `kelvinExponent::Real`: power $e$ of kelvin
  * `molExponent::Real`: power $f$ of mol
  * `candelaExponent::Real`: power $g$ of candela

# Constructor

```
BaseUnitExponents(; kg::Real=0, m::Real=0, s::Real=0, A::Real=0, K::Real=0, mol::Real=0, cd::Real=0)
```

# Raises Exceptions

  * `Core.DomainError`: if attempting to initialize any field with an infinite number

# Remarks

The constructor converts any exponent to `Int` if possible.

# Examples

The joule is defined as

$$
 1\,\mathrm{J} = 1\,\mathrm{kg}\,\mathrm{m^2}\,\mathrm{s^{-2}}.
$$

The corresponding `BaseUnitExponents` object is:

```jldoctest
julia> BaseUnitExponents(kg=1, m=2, s=-2)
BaseUnitExponents kg^1 m^2 s^-2 A^0 K^0 mol^0 cd^0
```

Calling the constructor without any keyword arguments returns exponents that correspond to a dimensionless unit:

```jldoctest
julia> BaseUnitExponents()
BaseUnitExponents kg^0 m^0 s^0 A^0 K^0 mol^0 cd^0
```
