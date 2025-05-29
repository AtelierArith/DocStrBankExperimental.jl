```
dictElement
```

Standard atomic weights of the elements 2021 - see IUPAC Technical Report

```
julia> dictElement
Dict{Int64, Tuple{String, String, Any}} with 102 entries:
  5  => ("boron", "B", 10.81)
  56 => ("barium", "Ba", 137.33)
  35 => ("bromine", "Br", 79.904)
  55 => ("caesium", "Cs", 132.91)
  60 => ("neodymium", "Nd", 144.24)
  30 => ("zinc", "Zn", 65.38)
   ⋮ =>  ⋮
```

#### Examples:

```
julia> get(dictElement, 37, nothing)
("rubidium", "Rb", 85.468)

julia> listElement("Rb", fmt=Info)
Element: rubidium
  symbol: Rb
  atomic number: Z = 37
  atomic weight (relative atomic mass): 85.468
```
