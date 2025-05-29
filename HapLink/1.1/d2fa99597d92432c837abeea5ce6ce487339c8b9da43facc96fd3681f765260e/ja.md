```
pseudoreads(sam::Union{AbstractString,AbstractPath}, consensus::NucleotideSeq)
```

`sam`に対して`consensus`に整列したときに存在するアライメントから[`Pseudoread`](@ref)のセットを作成します。
