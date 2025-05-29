```
test_wada_merge(basins, r) -> p
```

Test if the 2D array `basins` has the [Wada property](https://en.wikipedia.org/wiki/Lakes_of_Wada) using the merging technique of [Daza2018](@cite).

## Description

The technique consists in computing the generalized basins of each attractor. These new basins are formed with on of the basins and the union of the other basins. A new boundary is defined by these two objects. The algorithm then computes the distance between each boundaries of these basins pairwise. If all the boundaries are within some distance `r`, there is a unique boundary separating the basins and we have the wada property. The algorithm returns the maximum proportion of pixels of a boundary with distance strictly greater than `r` from another boundary.

If `p == 0`,  we have the Wada property for this value of `r`. If `p > 0`, the criteria to decide if the basins are Wada is left to the user. Numerical inaccuracies may be responsible for a small percentage of points with distance larger than `r`
