```
LinearMixedModel
```

Linear mixed-effects model representation

## Fields

  * `formula`: the formula for the model
  * `reterms`: a `Vector{AbstractReMat{T}}` of random-effects terms.
  * `Xymat`: horizontal concatenation of a full-rank fixed-effects model matrix `X` and response `y` as an `FeMat{T}`
  * `feterm`: the fixed-effects model matrix as an `FeTerm{T}`
  * `sqrtwts`: vector of square roots of the case weights.  Can be empty.
  * `parmap` : Vector{NTuple{3,Int}} of (block, row, column) mapping of θ to λ
  * `dims` : NamedTuple{(:n, :p, :nretrms),NTuple{3,Int}} of dimensions.  `p` is the rank of `X`, which may be smaller than `size(X, 2)`.
  * `A`: a `Vector{AbstractMatrix}` containing the row-major packed lower triangle of `hcat(Z,X,y)'hcat(Z,X,y)`
  * `L`: the blocked lower Cholesky factor of `Λ'AΛ+I` in the same Vector representation as `A`
  * `optsum`: an [`OptSummary`](@ref) object

## Properties

  * `θ` or `theta`: the covariance parameter vector used to form λ
  * `β` or `beta`: the fixed-effects coefficient vector
  * `λ` or `lambda`: a vector of lower triangular matrices repeated on the diagonal blocks of `Λ`
  * `σ` or `sigma`: current value of the standard deviation of the per-observation noise
  * `b`: random effects on the original scale, as a vector of matrices
  * `u`: random effects on the orthogonal scale, as a vector of matrices
  * `lowerbd`: lower bounds on the elements of θ
  * `X`: the fixed-effects model matrix
  * `y`: the response vector
