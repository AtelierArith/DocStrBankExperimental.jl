```
parent_molecule(::Atom)
parent_molecule(::Chain)
parent_molecule(::Fragment)
```

与えられたオブジェクトを含む `Molecule{T}` を返します。そのような分子が存在しない場合は `nothing` を返します。
