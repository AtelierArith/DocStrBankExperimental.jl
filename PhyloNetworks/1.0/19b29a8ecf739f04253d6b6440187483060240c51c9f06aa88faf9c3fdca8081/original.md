```
deleteaboveLSA!(net, preorder=true)
```

Delete edges and nodes above (ancestral to) the least stable ancestor (LSA) of the leaves in `net`. See [`leaststableancestor`](@ref) for the definition of the LSA. Output: modified network `net`.
