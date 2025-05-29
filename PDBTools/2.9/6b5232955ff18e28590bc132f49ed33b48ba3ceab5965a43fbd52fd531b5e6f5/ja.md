```
element_symbol_string(atom::Atom)
```

`Atom`構造体が与えられたときに、元素の記号を含む文字列を返します。

### 例

```jldoctest
julia> using PDBTools 

julia> at = Atom(name="NT3");

julia> element_symbol_string(at)
"N"
```
