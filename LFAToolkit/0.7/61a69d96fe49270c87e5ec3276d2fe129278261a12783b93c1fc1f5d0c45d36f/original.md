```julia
TensorBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    nodes1d,
    quadraturepoints1d,
    quadratureweights1d,
    interpolation1d,
    gradient1d;
    numberelements1d = 1,
)
```

Tensor product basis

# Arguments:

  * `numbernodes1d`:             number of nodes in 1 dimension
  * `numberquadraturepoints1d`:  number of quadrature points in 1 dimension
  * `numbercomponents`:          number of components
  * `dimension`:                 dimension of the basis
  * `nodes1d`:                   coordinates of the nodes in 1 dimension
  * `quadraturepoints1d`:        coordinates of the quadrature points in 1 dimension
  * `quadratureweights1d`:       quadrature weights in 1 dimension
  * `interpolation1d`:           interpolation matrix from nodes to quadrature points in 1 dimension
  * `gradient1d`:                gradient matrix from nodes to quadrature points in 1 dimension

# Keyword Arguments:

  * `numberelements1d = 1`:      number of subelements, for macroelement bases

# Returns:

  * tensor product basis object
