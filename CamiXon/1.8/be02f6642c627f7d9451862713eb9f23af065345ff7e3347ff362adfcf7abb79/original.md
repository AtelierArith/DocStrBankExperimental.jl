```
listIsotope(Z::Int, A::Int; fmt=Object)
```

Properties of isotopes with atomic number `Z` and atomic mass number `A`.

Output options: `fmt` =  `Object` (default), `String`, `Latex`, `Info`.

#### Example:

```
julia> listIsotope(1,3; fmt=Info);
Isotope: tritium-3
  symbol: ³T
  element: tritium
  atomic number: Z = 1
  atomic mass number: A = 3
  neutron number: N = 2
  rms nuclear charge radius: R = 1.7591 fm
  atomic mass: M = 3.016049281 amu
  nuclear spin: I = 1/2 ħ
  parity of nuclear state: π = even
  nuclear magnetic dipole moment: μI = 2.97896246 μN
  nuclear electric quadrupole moment: Q = 0.0 barn
  relative abundance: RA = trace
  lifetime: 12.33 years
```
