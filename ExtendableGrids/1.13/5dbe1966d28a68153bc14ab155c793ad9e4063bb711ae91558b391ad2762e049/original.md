```
seemingly_equal(grid1, grid2; sort=false, confidence=:full
```

Recursively check seeming equality of two grids. Seemingly means  that long arrays are only compared via random samples.

Keyword args:

  * `sort`: if true, sort grid points
  * `confidence`:  Confidence level: 

      * :low : Point numbers etc are the same
      * :full : all arrays are equal (besides the coordinate array, the arrays only have to be equal up to permutations)
