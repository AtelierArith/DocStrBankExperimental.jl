```
element_symbol(atom::Atom)
```

原子の名前または `Atom` 構造体を与えられたときの元素名のシンボルを返します。

### 例

```jldoctest
julia> using PDBTools 

julia> at = Atom(name="NT3");

julia> element_symbol(at)
:N
```
