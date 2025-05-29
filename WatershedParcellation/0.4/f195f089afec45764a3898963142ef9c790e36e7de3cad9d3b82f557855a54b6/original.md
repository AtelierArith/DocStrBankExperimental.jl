```
remove_weak_boundaries!(px, metric; threshold)
```

For each marginal or interstitial region separating two parcels in `px::Parcellation`, determine a merge priority for that region based on its edge strength: the median  value from `metric` (such as an edgemap) relative to the values in a neighborhood of  size `radius`. Iteratively merge pairs of parcels having such regions, starting with  the weakest edge and proceeding until the edge strength reaches or exceeds `threshold`.

Returns the number of boundaries that have been merged.
