```
merge_small_parcels!(px, metric; threshold)
```

For each `Parcel` in `px::Parcellation` smaller than `minsize` vertices, find its neighboring parcels (if any) and merge it with the one that has the weakest edge, i.e. the one for which the median value of `metric` (such as an edgemap) in the  interstitial region has the lowest value relative to values in a neighborhood of size `radius`.

Returns the number of merge operations that have occurred. 
