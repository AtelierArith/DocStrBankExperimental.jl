```
parent_secondary_structure(::Atom)
parent_secondary_structure(::Fragment)
parent_secondary_structure(::Nucleotide)
parent_secondary_structure(::Residue)
```

指定されたオブジェクトを含む`SecondaryStructure{T}`を返します。そのような二次構造が存在しない場合は`nothing`を返します。
