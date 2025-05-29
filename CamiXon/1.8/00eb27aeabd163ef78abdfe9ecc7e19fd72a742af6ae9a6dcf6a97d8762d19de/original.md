```
Isotope(symbol, name, Z, A, N, R, M, I, π, T½, mdm, eqm, ra)
```

Type with fields:

  * `.symbol`: symbol (`::String`)
  * `.name`: name (`::String`)
  * `.Z`:  atomic number (`::Int`)
  * `.A`:  atomic mass number in amu (`::Int`)
  * `.N`:  neutron number (`::Int`)
  * `.R`:  rms charge radius in Fermi (`::Float64`)
  * `.M`:  *atomic* mass in amu (`::Float64`)
  * `.I`:  nuclear spin in units of ħ  (`::Rational{Int}`)
  * `.π`:  parity of nuclear state (`::Int`)
  * `.T½`:  lifetime in years (`::Float64`)
  * `.mdm`: nuclear magnetic dipole moment (`::Float64`)
  * `.eqm`: nuclear electric quadrupole moment (`::Float64`)
  * `.ra`:  relative abundance in % (`::Float64`)

The type `Isotope` is best created with the function [`castIsotope`](@ref).
