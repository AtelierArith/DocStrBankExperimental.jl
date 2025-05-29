```
dictElement
```

元素の標準原子量 2021 - IUPAC技術報告を参照

```
julia> dictElement
Dict{Int64, Tuple{String, String, Any}} with 102 entries:
  5  => ("ホウ素", "B", 10.81)
  56 => ("バリウム", "Ba", 137.33)
  35 => ("臭素", "Br", 79.904)
  55 => ("セシウム", "Cs", 132.91)
  60 => ("ネオジム", "Nd", 144.24)
  30 => ("亜鉛", "Zn", 65.38)
   ⋮ =>  ⋮
```

#### 例:

```
julia> get(dictElement, 37, nothing)
("ルビジウム", "Rb", 85.468)

julia> listElement("Rb", fmt=Info)
Element: ルビジウム
  symbol: Rb
  atomic number: Z = 37
  atomic weight (relative atomic mass): 85.468
```
