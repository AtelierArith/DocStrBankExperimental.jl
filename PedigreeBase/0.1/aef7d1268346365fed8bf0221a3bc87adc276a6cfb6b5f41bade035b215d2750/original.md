```
permute_ped!(invp, pedlist [,idtable])
```

This function "renumbers" the animals by a permutation vector. It updates the code in `pedlist` according to the permutation list in `invp` as `invp[oldid]=newid`, which is generated with some functions like `find_ped_order`. The function also replaces IDs in `idtable` (optional). A code for unknown-parent group, which is usually greater than the maximum ID of real animals, remains in the new pedigree.
