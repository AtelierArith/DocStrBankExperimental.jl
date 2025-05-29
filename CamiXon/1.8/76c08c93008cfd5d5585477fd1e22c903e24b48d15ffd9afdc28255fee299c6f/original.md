```
castAtom(;Z=1, A=1, Q=0, msg=false)
castAtom(elt::String; A=1, Q=0, msg=false)
```

Create Atom with fields:

  * `.Z`:  atomic number (`::Int`)
  * `.A`:  atomic mass number in amu (`::Int`)
  * `.Q`:  ionic charge in a.u. (`::Int`)
  * `.Zc`:  Rydberg charge in a.u. (`::Int`)
  * `.element`:  (`::Element`)
  * `.isotope`:  (`::Isotope`)
  * `.config`:  electron configuration (`::String`)

`elt`: symbolic element name

#### Examples:

```
julia> castAtom("Rb"; A=87, Q=0) == castAtom(Z=37, A=87, Q=0)
true

julia> castAtom(Z=1, A=3, Q=0)
Atom(1, 3, 0, 1, Element("hydrogen", "H", 1.008), Isotope("³T", "tritium", 1, 3, 2, 1.7591, 3.016049281, 1//2, 1, 12.33, 2.97896246, 0.0, nothing), "1s¹")

julia> atom = castAtom(Z=1, A=3, Q=0, msg=true);
Element created: H, hydrogen, Z=1, weight=1.008
Isotope created: ³T, tritium, Z=1, A=3, N=2, R=1.7591, M=3.016049281, I=1/2⁺, μI=2.97896246, Q=0.0, RA=trace, (radioactive)
Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
  electron configuration: 1s¹
Atom created: Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
  electron configuration: 1s¹

julia> atom
Atom(1, 3, 0, 1, Element("hydrogen", "H", 1.008), Isotope("³T", "tritium", 1, 3, 2, 1.7591, 3.016049281, 1//2, 1, 12.33, 2.97896246, 0.0, nothing), "1s¹")

julia> string(atom.isotope.T½) * " seconds"
"12.33 seconds"
```
