```
isdisconnected(N::SpeciesInteractionNetwork{Unipartite{T}, <:Interactions}, sp::T, allow_self_interactions::Bool=true) where {T}
```

種が相互作用を持たない場合は `true` を返します。最後の引数（`allow_self_interactions`、デフォルトは `true`）は自己相互作用が許可されているかどうかを示します。`false` の場合、自己とだけ相互作用する種は切断されていると見なされます。
