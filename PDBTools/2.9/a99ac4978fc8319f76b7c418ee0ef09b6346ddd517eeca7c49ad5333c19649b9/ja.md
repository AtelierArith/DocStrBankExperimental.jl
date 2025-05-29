```
element_name(atom::Atom)
```

与えられた名前または `Atom` 構造体に基づいて、原子の元素名を返します。

### 例

```jldoctest
julia> using PDBTools

julia> at = Atom(name="NT3");

julia> element_name(at)
"Nitrogen"
```
