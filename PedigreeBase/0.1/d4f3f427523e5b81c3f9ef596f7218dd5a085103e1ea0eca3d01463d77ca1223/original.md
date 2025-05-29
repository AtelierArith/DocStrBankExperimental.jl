```
mgslist = mgs_ped(pedlist)
mgslist = mgs_ped(pedlist, males)
```

Create a pedigree list with sire and maternal-grandsire (MGS) only. The returned list `mgslist` has the same dimentions as `pedlist`, but the 2nd row has the MGS code. The UPG code in `pedlist` will be removed. The Boolean vector `males` indicates male (`true`) or female (`false`); by default, all animals will be treated as male.
