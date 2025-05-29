```
listAtom(Z::Int, A::Int, Q::Int[; fmt=Object])
```

Properties of atom with atomic number `Z`, atomic mass number `A`, ionic charge `Q`.

Output options: `fmt` =  `Object` (default), `String`, `Info`.

#### Example:

```
julia> listAtom("H", 3, 0) == listAtom(1, 3, 0)
true

julia> listAtom(1, 3, 0; fmt=Info)
Atom: tritium, neutral atom
  symbol: ³T
  atomic charge: Z = 1
  Rydberg charge: Zc = 1
```
