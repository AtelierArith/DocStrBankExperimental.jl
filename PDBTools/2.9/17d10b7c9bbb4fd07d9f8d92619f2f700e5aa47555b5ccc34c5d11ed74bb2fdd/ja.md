```
mass(atom::Atom)
mass(atoms::AbstractVector{<:Atoms})
```

与えられた名前または `Atom` 構造体の原子の質量、または `Atom` のベクトルの合計質量を返します。

質量が `Atom` 構造体のカスタムフィールドとして定義されている場合、それが返されます。そうでない場合、質量は原子名から推測される元素の質量から取得されます。

## 例

```jldoctest
julia> using PDBTools

julia> atoms = [ Atom(name="NT3"), Atom(name="CA") ];

julia> mass(atoms[1])
14.0067

julia> mass(atoms)
26.017699999999998
```
