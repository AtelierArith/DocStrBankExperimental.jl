```julia
TensorHProlongationBasis(
    coarsenodes1d,
    finenodes1d,
    numbercomponents,
    dimension,
    numberfineelements1d,
)
```

Tensor product h-prolongation basis

# Arguments:

  * `coarsenodes1d::AbstractArray{Float64,1}`:  coarse grid node coordinates in 1 dimension
  * `finenodes1d::AbstractArray{Float64,1}`:    fine grid node coordinates in 1 dimension
  * `numbercomponents::Int`:                    number of components
  * `dimension::Int`:                           dimension of basis
  * `numberfineelements1d::Int`:                number of fine grid elements

# Returns:

  * H1 Lagrange tensor product h-prolongation basis object
