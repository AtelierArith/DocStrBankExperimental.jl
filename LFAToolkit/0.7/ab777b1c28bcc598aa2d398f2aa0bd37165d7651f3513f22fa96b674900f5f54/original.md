```julia
TensorH1LagrangePProlongationBasis(
    numbercoarsenodes1d,
    numberfinenodes1d,
    numbercomponents,
    dimension,
)
```

Tensor product p-prolongation basis on Gauss-Legendre-Lobatto points

# Arguments:

  * `numbercoarsenodes1d::Int`:  number of coarse grid Gauss-Legendre-Lobatto nodes in 1 dimension
  * `numberfinenodes1d::Int`:    number of fine grid Gauss-Legendre-Lobatto nodes in 1 dimension
  * `numbercomponents::Int`:     number of components
  * `dimension::Int`:            dimension of basis

# Returns:

  * H1 Lagrange tensor product p-prolongation basis object

# Example:

```jldoctest
# generate H1 Lagrange tensor product p-prolongation basis
basisctof = TensorH1LagrangePProlongationBasis(2, 3, 1, 2);

# verify
println(basisctof)

# output

tensor product basis:
    numbernodes1d: 2
    numberquadraturepoints1d: 3
    numbercomponents: 1
    dimension: 2
```
