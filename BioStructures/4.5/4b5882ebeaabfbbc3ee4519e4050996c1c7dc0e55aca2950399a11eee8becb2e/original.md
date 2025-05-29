```
chainid!(ch, id)
chainid!(res, id)
```

Set the chain ID of a `Chain` or an `AbstractResidue` to a new `String`.

If a chain with this ID already exists, it will be removed from its current chain and added to that chain. If a chain with this ID does not exist, a new chain will be added to the model and this residue will be added to it. If moving this residue from a chain to a new chain leaves the old chain without residues, the old chain will be removed from the `Model`.
