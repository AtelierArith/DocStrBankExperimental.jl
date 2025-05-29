```
rotate(mat::AbstractMatrix, α::Real; <keyword arguments>)
```

Rotate matrix `mat` about the center of angle `α` given in degrees. If `rows` and `cols` are not given, the rotated matrix has the same dimensions of the original matrix.

# Arguments

  * `mat`: matrix to rotate.
  * `α`: angle in degrees.
  * `rows=nothing`: number of rows of the rotated matrix.
  * `cols=nothing`: number of columns of the rotated matrix.
  * `interpolation`: interpolation strategy. By default is   `BilinearInterpolation`.
