```julia
NonTensorBasis(
    numbernodes,
    numberquadraturepoints,
    numbercomponents,
    dimension,
    nodes,
    quadraturepoints,
    quadratureweights,
    interpolation,
    gradient;
    numberelements = 1,
)
```

Non-tensor basis

# Arguments:

  * `numbernodes`:             number of nodes
  * `numberquadraturepoints`:  number of quadrature points
  * `numbercomponents`:        number of components
  * `dimension`:               dimension of the basis
  * `nodes`:                   coordinates of the nodes
  * `quadraturepoints`:        coordinates of the quadrature points
  * `quadratureweights`:       quadrature weights
  * `interpolation`:           interpolation matrix from nodes to quadrature points
  * `gradient`:                gradient matrix from nodes to quadrature points

# Keyword Arguments:

  * `numberelements = 1`:      number of subelements, for macroelement bases

# Returns:

  * non-tensor product basis object
