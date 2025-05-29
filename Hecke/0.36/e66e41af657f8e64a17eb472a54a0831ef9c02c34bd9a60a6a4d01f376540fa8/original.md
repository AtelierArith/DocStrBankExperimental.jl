```
hom_direct_sum(G::FinGenAbGroup, H::FinGenAbGroup, V::Vector{<:Map{FinGenAbGroup, FinGenAbGroup}})
```

For groups `G = prod G_i` and `H = prod H_i` as well as maps `V_i: G_i -> H_i`, build the induced map from `G -> H`.
