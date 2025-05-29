```julia
TensorH1LagrangeMacroBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension,
    numberelements1;
    collocatedquadrature = false,
    mapping = nothing,
)
```

Tensor product macro-element basis on Gauss-Legendre-Lobatto points with Gauss-Legendre (default) or Gauss-Legendre-Lobatto quadrature points

# Arguments:

  * `numbernodes1d::Int`:             number of Gauss-Legendre-Lobatto nodes in 1 dimension
  * `numberquadraturepoints1d::Int`:  number of quadrature points in 1 dimension
  * `numbercomponents::Int`:          number of components
  * `dimension::Int`:                 dimension of basis
  * `numberelements1d::Int`:          number of elements in macro-element

# Keyword Arguments:

  * `collocatedquadrature::Bool = false`:                          Gauss-Legendre (`false`) or Gauss-Legendre-Lobatto (`true`) quadrature points
  * `mapping::Union{Tuple{Function,Function},Nothing} = nothing`:  quadrature point mapping - sausage, Kosloff-Talezer, Hale-Trefethen strip, or no transformation

# Returns:

  * H1 Lagrange tensor product macro-element basis object

# Example:

```jldoctest
# generate H1 Lagrange tensor macro-element product basis
basis = TensorH1LagrangeMacroBasis(4, 4, 1, 2, 2);

# generate basis with Gauss-Legendre quadrature points
basis = TensorH1LagrangeMacroBasis(4, 4, 1, 2, 2; collocatedquadrature = true);

# verify
println(basis)

# output

macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
```
