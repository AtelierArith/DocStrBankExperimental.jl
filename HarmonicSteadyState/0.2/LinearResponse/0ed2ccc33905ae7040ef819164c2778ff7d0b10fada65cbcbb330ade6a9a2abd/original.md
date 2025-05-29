```
eigenvectors(res::Result, branch; class=["physical"])
```

get_Jacobiannch to analyze

  * `class=["physical"]`: Filter for solution classes to include, defaults to physical solutions

# Returns

  * Vector of filtered eigenvectors along the solution branch

# Notes

  * Currently only supports 1-dimensional parameter sweeps (D=1)
  * Will throw an error if branch contains NaN values
  * Eigenvectors are filtered based on the specified solution classes
