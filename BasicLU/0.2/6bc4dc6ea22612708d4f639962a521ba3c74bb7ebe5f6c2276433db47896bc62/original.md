```
basis, F = maxvolbasis(A::SparseMatrixCSC{Float64, Int64}; lindeptol::Float64=1e-8,
                       volumetol::Float64=2.0, maxpass::Int64=2, verbose::Bool=true) -> Vector{Int64}, LUFactor
```

Find a set of column indices for the matrix `AI = [A I]` such that `AI[:,basis]` is square and nonsingular and the number of slack columns in the basis is minimum (this is the row rank deficiency of `A`). Return the vector of column indices of `AI` which form the basis matrix and a `LUFactor` which holds a factorization of the basis matrix.

Method: Scale the slack columns of `AI` by `lindeptol` and try to find a maximum volume basis for this matrix by making at most `maxpass` calls to [`maxvolume`](@ref). If `verbose` is true, then print the number of basis updates after each call.
