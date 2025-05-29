```
dictAtomicNumber
```

```
julia> dictAtomicNumber
Dict{String, Int64} with 102 entries: 
  "Pd" => 46
  "Si" => 14
  "C"  => 6
  "P"  => 15
  "Nb" => 41
    ⋮  =>  ⋮
```

#### 例:

```
julia> Z = get(dictAtomicNumber, "Rb", nothing)
37

julia> listElement(Z; fmt=Info)
Element: ルビジウム
symbol: Rb
atomic number: Z = 37
atomic weight (relative atomic mass): 85.468
```
