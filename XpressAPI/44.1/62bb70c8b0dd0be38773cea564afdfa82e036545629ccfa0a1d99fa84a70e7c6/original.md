```
XPRSgetiisdata(prob, iis, rowind, colind, contype, bndtype, duals, djs, isolationrows, isolationcols)::nrows, ncols, rowind, colind, contype, bndtype, duals, djs, isolationrows, isolationcols
```

Returns information for an Irreducible Infeasible Set: size, variables and constraints (row and column vectors), and conflicting sides of the variables.

For pure linear problems there is also information on duals, reduced costs and isolations.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `iis::Integer`: The ordinal number of the IIS to get data for.
  * `rowind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Indices of rows in the IIS. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Indices of bounds (columns) in the IIS. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `contype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Sense of rows in the IIS: Lfor less or equal row; Gfor greater or equal row. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `bndtype::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: Sense of bound in the IIS: Ufor upper bound; Lfor lower bound. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: The dual multipliers associated with the rows. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: The dual multipliers (reduced costs) associated with the bounds. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `isolationrows::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: The isolation status of the rows: -1if isolation information is not available for row (run iis isolations); 0if row is not in isolation; 1if row is in isolation. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `isolationcols::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: The isolation status of the bounds: -1if isolation information is not available for column (run iis isolations); 0if column is not in isolation; 1if column is in isolation. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `nrows::Int32`: Pointer to an integer where the number of rows in the IIS will be returned.
  * `ncols::Int32`: Pointer to an integer where the number of bounds in the IIS will be returned.
  * `rowind::Union{Nothing,AbstractVector{Int32}}`: Indices of rows in the IIS.
  * `colind::Union{Nothing,AbstractVector{Int32}}`: Indices of bounds (columns) in the IIS.
  * `contype::Union{Nothing,AbstractVector{Cchar}}`: Sense of rows in the IIS: Lfor less or equal row; Gfor greater or equal row.
  * `bndtype::Union{Nothing,AbstractVector{Cchar}}`: Sense of bound in the IIS: Ufor upper bound; Lfor lower bound.
  * `duals::Union{Nothing,AbstractVector{Float64}}`: The dual multipliers associated with the rows.
  * `djs::Union{Nothing,AbstractVector{Float64}}`: The dual multipliers (reduced costs) associated with the bounds.
  * `isolationrows::Union{Nothing,AbstractVector{Cchar}}`: The isolation status of the rows: -1if isolation information is not available for row (run iis isolations); 0if row is not in isolation; 1if row is in isolation.
  * `isolationcols::Union{Nothing,AbstractVector{Cchar}}`: The isolation status of the bounds: -1if isolation information is not available for column (run iis isolations); 0if column is not in isolation; 1if column is in isolation.

See also the documentation of the correponding function [XPRSgetiisdata](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetiisdata.html) in the C API.
