```
Atom(Z, A, Q, Zc, element, isotope, config)
```

Type with fields:

  * `.Z`:  atomic number (`::Int`)
  * `.A`:  atomic mass number in amu (`::Int`)
  * `.Q`:  ionic charge in a.u. (`::Int`)
  * `.Zc`:  Rydberg charge in a.u. (`::Int`)
  * `.element`:  (`::Element`)
  * `.isotope`:  (`::Isotope`)
  * `.config`:  electron configuration (`::String`)

The type `Atom` is best created with the function [`castAtom`](@ref).
