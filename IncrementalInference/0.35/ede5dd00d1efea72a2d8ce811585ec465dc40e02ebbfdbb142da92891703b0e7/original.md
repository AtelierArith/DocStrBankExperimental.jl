```julia
loadTree()
loadTree(filepath)

```

EXPERIMENTAL, Save a Bayes (Junction) tree object to file.

Notes

  * Converts and saves to JLD2 format a set of `PackedBayesTreeNodeData` objects.
  * IIF issue #481

Related

[`saveTree`](@ref), [`saveDFG`](@ref), [`loadDFG`](@ref), `BSON.@save`, `BSON.@load`
