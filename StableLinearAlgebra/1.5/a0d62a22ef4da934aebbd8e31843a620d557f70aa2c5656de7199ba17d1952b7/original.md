```
LDRWorkspace{T<:Number}
```

A workspace to avoid dyanmic memory allocations when performing computations with a [`LDR`](@ref) factorization.

# Fields

  * `qr_ws::QRWorkspace{T,E}`: [`QRWorkspace`](@ref) for calculating column pivoted QR factorization without dynamic memory allocations.
  * `lu_ws::LUWorkspace{T}`: [`LUWorkspace`](@ref) for calculating LU factorization without dynamic memory allocations.
  * `M::Matrix{T}`: Temporary storage matrix for avoiding dynamic memory allocations. This matrix is used/modified when a [`LDR`](@ref) factorization is calculated.
  * `M′::Matrix{T}`: Temporary storage matrix for avoiding dynamic memory allocations.
  * `M″::Matrix{T}`: Temporary storage matrix for avoiding dynamic memory allocations.
  * `v::Vector{T}`: Temporary storage vector for avoiding dynamic memory allocations.
