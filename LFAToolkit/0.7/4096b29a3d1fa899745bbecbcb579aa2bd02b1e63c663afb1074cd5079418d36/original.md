```julia
TensorH1LagrangeBasis(
    numbernodes1d,
    numberquadraturepoints1d,
    numbercomponents,
    dimension;
    collocatedquadrature = false,
    mapping = nothing,
)
```

Tensor product basis on Gauss-Legendre-Lobatto points with Gauss-Legendre (default) or Gauss-Legendre-Lobatto quadrature points

# Arguments:

  * `numbernodes1d::Int`:             number of Gauss-Legendre-Lobatto nodes in 1 dimension
  * `numberquadraturepoints1d::Int`:  number of quadrature points in 1 dimension
  * `numbercomponents::Int`:          number of components
  * `dimension::Int`:                 dimension of basis

# Keyword Arguments:

  * `collocatedquadrature::Bool = false`:                          Gauss-Legendre (`false`) or Gauss-Legendre-Lobatto (`true`) quadrature points
  * `mapping::Union{Tuple{Function,Function},Nothing} = nothing`:  quadrature point mapping - sausage, Kosloff-Talezer, Hale-Trefethen strip, or no transformation

# Returns:

  * H1 Lagrange tensor product basis object

# Example:

```jldoctest
# generate transformed basis from conformal maps with Gauss-Legendre quadrature points
mapping = hale_trefethen_strip_transformation(1.4);
basis = TensorH1LagrangeBasis(4, 4, 3, 2, collocatedquadrature = true, mapping = mapping);

# verify
println(basis)

# output

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
```
