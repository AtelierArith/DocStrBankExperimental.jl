```julia
TensorH1UniformHProlongationMacroBasis(
    numbernodes1d,
    numbercomponents,
    dimension,
    numbercoarseelements1d,
    numberfineelements1d,
)
```

Tensor product macro-element h-prolongation basis on uniformly spaced points

# Arguments:

  * `numbernodes1d::Int`:           number of uniformly spaced nodes per element
  * `numbercomponents::Int`:        number of components
  * `dimension::Int`:               dimension of basis
  * `numbercoarseelements1d::Int`:  number of coarse grid elements in macro-element
  * `numberfineelements1d::Int`:    number of fine grid elements in macro-element

# Returns:

  * H1 Lagrange tensor product h-prolongation macro-element basis on uniformly spaced nodes object

# Example:

```jldoctest
# generate H1 Lagrange tensor product h-prolongation macro-element basis on uniformly spaced nodes
basis = TensorH1UniformHProlongationMacroBasis(4, 1, 2, 2, 4);

# verify
println(basis)

# output

macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 13
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
```
