```julia
TensorH1LagrangeHProlongationBasis(
    numbernodes1d,
    numbercomponents,
    dimension,
    numberfineelements1d,
)
```

Tensor product h-prolongation basis on Gauss-Legendre-Lobatto points

# Arguments:

  * `numbernodes1d::Int`:         number of Gauss-Legendre-Lobatto nodes in 1 dimension per element
  * `numbercomponents::Int`:      number of components
  * `dimension::Int`:             dimension of basis
  * `numberfineelements1d::Int`:  number of fine grid elements

# Returns:

  * H1 Lagrange tensor product h-prolongation basis object

# Example:

```jldoctest
# generate H1 Lagrange tensor product h-prolongation basis
basis = TensorH1LagrangeHProlongationBasis(4, 3, 2, 2);

# verify
println(basis)

# output

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 7
    numbercomponents: 3
    dimension: 2
```
