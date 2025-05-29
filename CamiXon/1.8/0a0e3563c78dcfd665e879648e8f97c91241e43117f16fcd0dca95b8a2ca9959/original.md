```
listElement(Z::Int[; fmt=Object])
listElement(elt::String[; fmt=Object])
```

Properties of element with atomic number `Z` and symbolic name `elt`

Output options: `fmt` =  `Object` (default), `String`, `Info`.

#### Example:

```
julia> listElement("H") == listElement(1)
true

julia> listElement(1; fmt=Info)
Element: hydrogen
  symbol: H
  atomic number: Z = 1
  atomic weight (relative atomic mass): 1.008
```
