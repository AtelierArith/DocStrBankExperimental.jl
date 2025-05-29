```
getlevel(meta::MetaVLSV, cid::Int) -> Int
```

Return the AMR level of a given cell ID `cid`.

!!! warning
    This function does not check if the VLSV file of `meta` actually contains `cid`; it may be shadowed by refined children.

