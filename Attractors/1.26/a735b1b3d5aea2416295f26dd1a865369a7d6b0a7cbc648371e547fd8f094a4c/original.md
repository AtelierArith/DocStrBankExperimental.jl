```
haussdorff_distance(M1, M2) -> hd
```

Compute the Hausdorff distance between two binary matrices of the same size. First a distance matrix is computed using `distance_matrix` for each matrix M1 and M2. The entries of this matrix are the distance in L1 metric to the closest 0 pixel in the initial matrix. The distance being 0 if it belongs to the basin with id 0.
