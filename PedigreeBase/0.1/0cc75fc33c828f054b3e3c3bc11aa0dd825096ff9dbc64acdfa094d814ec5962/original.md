```
perm,invp = find_ped_order(pedlist [,start])
```

Traverses the pedigree and finds a permutation so that the ancestors precede their progeny. The resulting vector `perm` associates the current ID with the new ID i.e., `perm[newid]=oldid`. The vector `invp` has the inverse permutation i.e. `invp[oldid]=newid`. By default, the function takes each animal as the starting animal. When supplying an optional vector `start` with starting IDs, the tracing starts only with these progeny. In this case, `perm` and `invp` will include `0` for non-tracked animals.
