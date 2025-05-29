```
hom_direct_sum(G::FinGenAbGroup, H::FinGenAbGroup, V::Vector{<:Map{FinGenAbGroup, FinGenAbGroup}})
```

群 `G = prod G_i` および `H = prod H_i` とマップ `V_i: G_i -> H_i` に対して、`G -> H` から誘導されたマップを構築します。
