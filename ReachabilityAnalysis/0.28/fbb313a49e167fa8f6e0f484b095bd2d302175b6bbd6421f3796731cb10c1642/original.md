```
BoxClustering{PI, PO} <: AbstractClusteringMethod{P}
```

### Notes

This method first takes a lazy convex hull for the given partition, then computes a tight hyperrectangular approximation for each element in the partition.
