```
listElements(Z1::Int, Z2::Int[; fmt=Object])
listElements(itr::UnitRange{Int}; fmt=Object)
```

原子番号が範囲 `itr = Z1:Z2` の要素のプロパティ。

出力オプション: `fmt` =  `Object` (デフォルト), `String`, `Info`。

#### 例

```
julia> listElements(1,3) == listElements(1:3)
true

julia> listElements(1:3; fmt=Info);
Element: hydrogen
  symbol: H
  atomic number: Z = 1
  atomic weight (relative atomic mass): 1.008
Element: helium
  symbol: He
  atomic number: Z = 2
  atomic weight (relative atomic mass): 4.0026
Element: lithium
  symbol: Li
  atomic number: Z = 3
  atomic weight (relative atomic mass): 6.94

julia> listElements(1:3; fmt=String)
3-element Vector{Any}:
 "H, hydrogen, Z=1, weight=1.008"
 "He, helium, Z=2, weight=4.0026"
 "Li, lithium, Z=3, weight=6.94"    
```
