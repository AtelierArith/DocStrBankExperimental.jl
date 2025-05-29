```
castIsotope(;Z=1, A=1, msg=false)
castIsotope(elt::String; A=1, msg=false)
```

Create Isotope with fields

  * `.symbol`: symbol (`::String`)
  * `.name`: symbol (`::String`)
  * `.Z`:  atomic number (`::Int`)
  * `.A`:  atomic mass number in amu (`::Int`)
  * `.N`:  neutron number (`::Int`)
  * `.R`:  rms charge radius in Fermi (`::Float64`)
  * `.M`:  atomic mass in amu (`::Float64`)
  * `.I`:  nuclear spin in units of ħ (`::Rational{Int}`)
  * `.π`:  parity of nuclear state (`::Int`)
  * `.ra`:  relative abundance in % (`::Float64`)
  * `.mdm`: nuclear magnetic dipole moment (`::Float64`)
  * `.eqm`: nuclear electric quadrupole moment (`::Float64`)
  * `.T½`:  lifetime in years (`::Float64`)

`Z`: atomic number (nuclear charge number) `elt`: symbolic element name

#### Examples:

```
julia> castIsotope("Rb"; A=87) == castIsotope(Z=37, A=87)
true

julia> isotope = castIsotope(Z=1, A=3)
Isotope("³T", "tritium", 1, 3, 2, 1.7591, 3.016049281, 1//2, 1, 12.33, 2.97896246, 0.0, nothing)

julia> string(isotope.T½) *  " seconds"
"12.33 seconds"

julia> castIsotope(Z=1, A=3, msg=true);
Isotope created: ³T, tritium, Z=1, A=3, N=2, R=1.7591, M=3.016049281, I=1/2⁺, μI=2.97896246, Q=0.0, RA=trace, (radioactive)
```
