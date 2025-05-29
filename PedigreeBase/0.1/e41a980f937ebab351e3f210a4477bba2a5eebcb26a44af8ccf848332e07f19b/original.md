```
perm,invp,subpedlist = subset_ped(pedlist,idlist)
```

Creates a subset of pedigree list `pedlist` with two permutation vectors: `perm[newid]=oldid` and invp[oldid]=newid`. The subset includes the animals listed in`idlist` and their ancestors. The subset pedigree is chronologically sorted.

This function is a wrapper for `find_ped_order` and `extract_ped`. See the functions fro details.
