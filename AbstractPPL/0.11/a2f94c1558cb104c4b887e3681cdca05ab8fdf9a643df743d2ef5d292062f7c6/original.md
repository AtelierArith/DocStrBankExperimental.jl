```
subsumes(u::VarName, v::VarName)
```

Check whether the variable name `v` describes a sub-range of the variable `u`.  Supported indexing:

  * Scalar:

```jldoctest   julia> subsumes(@varname(x), @varname(x[1, 2]))   true

julia> subsumes(@varname(x[1, 2]), @varname(x[1, 2][3]))   true   ```

  * Array of scalar: basically everything that fulfills `issubset`.

```jldoctest   julia> subsumes(@varname(x[[1, 2], 3]), @varname(x[1, 3]))   true

julia> subsumes(@varname(x[1:3]), @varname(x[2][1]))   true   ```

  * Slices:

`jldoctest   julia> subsumes(@varname(x[2, :]), @varname(x[2, 10][1]))   true`

Currently *not* supported are: 

  * Boolean indexing, literal `CartesianIndex` (these could be added, though)
  * Linear indexing of multidimensional arrays: `x[4]` does not subsume `x[2, 2]` for a matrix `x`
  * Trailing ones: `x[2, 1]` does not subsume `x[2]` for a vector `x`
