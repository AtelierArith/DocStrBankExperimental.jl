```julia
TensorH1UniformMacroBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    numberelements1d,
)
```

Tensor product macro-element basis on uniformly points with Gauss-Legendre quadrature

# Arguments:

  * `numbernodes1d::Int`:             number of uniformly spaced nodes in 1 dimension
  * `numberquadraturepoints1d::Int`:  number of Gauss-Legendre quadrature points in 1 dimension
  * `numbercomponents::Int`:          number of components
  * `dimension::Int`:                 dimension of basis
  * `numberelements1d::Int`:          number of elements in macro-element

# Returns:

  * H1 Lagrange tensor product macro-element basis on uniformly space nodes object

# Example:

```jldoctest
# generate H1 Lagrange tensor product macro-element basis on uniformly spaced nodes
basis = TensorH1UniformMacroBasis(4, 3, 1, 2, 2);

# verify
println(basis)

# output

macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 6
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
```
