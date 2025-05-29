```
newlist,newtable = extract_ped(invp, pedlist ,idtable)
newlist          = extract_ped(invp, pedlist)
```

Extract the code in `pedlist` according to the permutation list in `invp` as `invp[oldid]=newid`, which is generated with some functions like `find_ped_order`. With optional `idtable`, it will also return with the new table. The function re-assigns the code to animals in `newlist`. The behavior is similar to `permute_ped`, but this function supports reducing the amount of pedigree.
