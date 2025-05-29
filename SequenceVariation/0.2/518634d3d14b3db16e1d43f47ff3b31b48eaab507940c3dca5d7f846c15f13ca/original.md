```
translate(var::Variation{S,T}, aln::PairwiseAlignment{S,S}) where {S,T}
```

Convert the difference in `var` to a new reference sequence based upon `aln`. `aln` is the alignment of the old reference (`aln.b`) and the new reference sequence (`aln.seq`). Returns the new [`Variation`](@ref).
