```
atomic_number(atom::Atom)
```

原子の `Atom` 構造体から原子番号を返します。

### 例

```jldoctest
julia> using PDBTools

julia> at = Atom(name="NT3");

julia> atomic_number(at)
7
```
