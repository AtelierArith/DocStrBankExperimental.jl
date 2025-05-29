```
element(atom::Atom)
```

与えられた `Atom` 構造体の原子の要素記号を文字列として返します。`pdb_element` が空であるか "X" の場合、要素は原子名から推測されます。それ以外の場合、`pdb_element` が返されます。

### 例

```jldoctest
julia> using PDBTools

julia> at = Atom(name="NT3");

julia> element(at)
"N"
```
