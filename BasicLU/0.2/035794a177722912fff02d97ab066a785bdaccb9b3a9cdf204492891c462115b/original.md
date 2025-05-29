```
nupdate = maxvolume(F::LUFactor, A::SparseMatrixCSC{Float64, Int64}, basis::Vector{Int64}, volumetol::Float64=2.0) -> Int64
```

Given an initial basis such that `A[:,basis]` is square and nonsingular, make one pass over the nonbasic columns of `A` and pivot each column into the basis when it increases the absolute value of the determinant of the basis matrix by more than a factor `volumetol`. On return `basis` has been updated. Return the number of basis updates performed.
