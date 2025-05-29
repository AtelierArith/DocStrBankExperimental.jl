```
XPRSgetqrowqmatrixtriplets(prob, row, rowqcol1, rowqcol2, rowqcoef)::ncoefs, rowqcol1, rowqcol2, rowqcoef
```

Returns the nonzeros in a quadratic constraint coefficients matrix as triplets (index pairs with coefficients).

To achieve maximum efficiency, `XPRSgetqrowqmatrixtriplets` returns the lower triangular part of this matrix only.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `row::Integer`: Index of the row for which the quadratic coefficients are to be returned.
  * `rowqcol1::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: First index in the triplets. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `rowqcol2::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Second index in the triplets. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `rowqcoef::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Coefficients in the triplets. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `ncoefs::Int32`: Argument used to return the number of quadratic coefficients in the row.
  * `rowqcol1::Union{Nothing,AbstractVector{Int32}}`: First index in the triplets.
  * `rowqcol2::Union{Nothing,AbstractVector{Int32}}`: Second index in the triplets.
  * `rowqcoef::Union{Nothing,AbstractVector{Float64}}`: Coefficients in the triplets.

See also the documentation of the correponding function [XPRSgetqrowqmatrixtriplets](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetqrowqmatrixtriplets.html) in the C API.
