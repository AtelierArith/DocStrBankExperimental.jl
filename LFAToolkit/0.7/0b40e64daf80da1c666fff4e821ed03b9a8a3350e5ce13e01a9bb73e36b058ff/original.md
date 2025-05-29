```julia
TensorH1UniformBasis(numbernodes1d, numberquadraturepoints1d, numbercomponents, dimension)
```

Tensor product basis on uniformly spaced points with Gauss-Legendre quadrature points

# Arguments:

  * `numbernodes1d::Int`:             number of uniformly spaced nodes in 1 dimension
  * `numberquadraturepoints1d::Int`:  number of Gauss-Legendre quadrature points in 1 dimension
  * `numbercomponents::Int`:          number of components
  * `dimension::Int`:                 dimension of basis

# Returns:

  * H1 Lagrange tensor product basis on uniformly spaced nodes object

# Example:

```jldoctest
# generate H1 Lagrange tensor product basis on uniformly spaced nodes
basis = TensorH1UniformBasis(4, 3, 2, 1);

# verify
println(basis)

# output

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 3
    numbercomponents: 2
    dimension: 1
```
