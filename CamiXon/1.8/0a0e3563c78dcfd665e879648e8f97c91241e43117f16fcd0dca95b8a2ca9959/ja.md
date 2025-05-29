```
listElement(Z::Int[; fmt=Object])
listElement(elt::String[; fmt=Object])
```

原子番号 `Z` と記号名 `elt` を持つ元素のプロパティ

出力オプション: `fmt` =  `Object` (デフォルト), `String`, `Info`.

#### 例:

```
julia> listElement("H") == listElement(1)
true

julia> listElement(1; fmt=Info)
Element: hydrogen
  symbol: H
  atomic number: Z = 1
  atomic weight (relative atomic mass): 1.008
```
