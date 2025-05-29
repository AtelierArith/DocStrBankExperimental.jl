```julia
saveTree(treel)
saveTree(treel, filepath)

```

EXPERIMENTAL, Save a Bayes (Junction) tree object to file.

Notes

  * Converts and saves to BSON format a set of `PackedBayesTreeNodeData` objects.
  * IIF issue #481

Related

[`loadTree`](@ref), [`saveDFG`](@ref), [`loadDFG`](@ref), `BSON.@save`, `BSON.@load`
