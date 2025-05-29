```
errors(mode, coords, unf_coords; search=:knn, neigh=16, maxerr=5)
```

Unfolding distorts the original distances between neighbor points. This function returns two types of results depending on `mode`.

If `mode = :ids`, this gives the IDs of the points above and below the `maxerr` threshold as a tuple such that (ids*passed*the*tests, ids*not*passed*the_tests)

If `mode = :dists`, this function output the difference of the expected distance for each pair analyzed in the neighborhood. Can be used as input in a boxplot to verify distortions.

## Parameters:

  * `mode`       - type of error, :ids or :dists.
  * `coords`     - coordinate matrix of the points before unfolding.
  * `unf_coords` - coordinate matrix of the points after unfolding.
  * `search`     - type of neighborhood, :knn or :radius.
  * `neigh`      - number of neighbors or radius used to make the validations.
  * `maxerr`     - the maximum accepted absolute difference of the distances if mode = :ids.
