```
parent_nucleotide(::Atom)
```

指定された原子を含む `Fragment{T}` を返します。該当するフラグメントが存在しない場合や、フラグメントが [`FragmentVariant.Nucleotide`](@ref FragmentVariant) でない場合は `nothing` を返します。
