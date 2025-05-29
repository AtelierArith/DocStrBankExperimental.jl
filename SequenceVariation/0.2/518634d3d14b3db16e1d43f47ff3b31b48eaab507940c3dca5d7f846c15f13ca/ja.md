```
translate(var::Variation{S,T}, aln::PairwiseAlignment{S,S}) where {S,T}
```

`var`の差分を`aln`に基づいて新しい参照配列に変換します。`aln`は古い参照（`aln.b`）と新しい参照配列（`aln.seq`）のアライメントです。新しい[`Variation`](@ref)を返します。
