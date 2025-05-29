```julia
TensorH1UniformHProlongationBasis(
    numbernodes1d,
    numbercomponents,
    dimension,
    numberfineelements1d,
)
```

Tensor product h-prolongation basis on uniformly spaced points

# Arguments:

  * `numbernodes1d::Int`:         number of uniformly spaced nodes per element
  * `numbercomponents::Int`:      number of components
  * `dimension::Int`:             dimension of basis
  * `numberfineelements1d::Int`:  number of fine grid elements

# Returns:

  * H1 Lagrange tensor product h-prolongation basis on uniformly spaced nodes object

# Example:

```jldoctest
# generate H1 Lagrange tensor product h-prolongation basis on uniformly spaced nodes
basis = TensorH1UniformHProlongationBasis(4, 3, 2, 2);

# verify
println(basis)

# output

tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 7
    numbercomponents: 3
    dimension: 2
```
