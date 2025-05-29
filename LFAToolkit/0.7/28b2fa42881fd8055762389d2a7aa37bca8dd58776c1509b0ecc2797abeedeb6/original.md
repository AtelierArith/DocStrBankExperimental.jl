```julia
TensorMacroElementBasisFrom1D(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    numberelements1d,
    basis1dmicro;
    overlapquadraturepoints = false,
)
```

Tensor product macro-element basis from 1d single element tensor product basis

# Arguments:

  * `numbernodes1d::Int`:             number of basis nodes in 1 dimension
  * `numberquadraturepoints1d::Int`:  number of quadrature points in 1 dimension
  * `numbercomponents::Int`:          number of components
  * `dimension::Int`:                 dimension of basis
  * `numberelements1d::Int`:          number of elements in macro-element
  * `basis1dmicro::TensorBasis`:      1d micro element basis to replicate

# Keyword Arguments:

  * `overlapquadraturepoints::Bool = false`:  overlap quadrature points between elements, for prolongation

# Returns:

  * tensor product macro-element basis object
