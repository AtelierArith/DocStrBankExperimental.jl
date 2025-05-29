```
translate(hap::Haplotype{S,T}, aln::PairwiseAlignment{S,S}) where {S,T}
```

`hap`の変異を`aln`に基づいて新しい参照配列に変換します。アライメントルールは[`translate(::Variation, PairwiseAlignment)`](@ref translate(::Variation{S,T}, ::PairwiseAlignment{S,S}) where {S,T})の規則に従います。開始または終了のインデルは保持されない場合があります。新しい[`Haplotype`](@ref)を返します。
