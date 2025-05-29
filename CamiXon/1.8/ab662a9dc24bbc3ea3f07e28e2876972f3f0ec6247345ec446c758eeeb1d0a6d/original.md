```
listAtoms(Z1::Int, Z2::Int, Q::Int[; fmt=Object])
```

Properties of atoms with atomic number in the range `Z1:Z3` and ionic charge `Q`.

Output options: `fmt` =  `Object` (default), `String`, `Info`.

#### Example

```
julia> listAtoms(1,3,0) == listAtoms(1:3,0)
true

julia> listAtoms(1:1, 0; fmt=Info);
Atom: hydrogen, neutral atom
  symbol: ¹H
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
Atom: deuterium, neutral atom
  symbol: ²D
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
```
