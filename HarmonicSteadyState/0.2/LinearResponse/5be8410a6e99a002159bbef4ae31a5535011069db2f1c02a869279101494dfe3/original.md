```
eigenvalues(res::Result, branch; class=["physical"])
```

Calculate the eigenvalues of the Jacobian matrix of the harmonic equations of a `branch` for a one dimensional sweep in the [Result](@ref) struct.

# Arguments

  * `res::Result`: Result object containing solutions and jacobian information
  * `branch`: Index of the solution branch to analyze
  * `class=["physical"]`: Filter for solution classes to include, defaults to physical solutions

# Returns

  * Vector of filtered eigenvalues along the solution branch

# Notes

  * Currently only supports 1-dimensional parameter sweeps (D=1)
  * Will throw an error if branch contains NaN values
  * Eigenvalues are filtered based on the specified solution classes
