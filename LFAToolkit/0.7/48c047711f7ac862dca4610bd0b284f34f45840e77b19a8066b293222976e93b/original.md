```julia
LumpedBDDC(operator)
```

Lumped BDDC preconditioner for finite element operators

# Arguments:

  * `operator::Operator`:  finite element operator to precondition

# Returns:

  * lumped BDDC preconditioner object

# Example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);

# operator
finediffusion = GalleryOperator("diffusion", 5, 5, mesh);

# preconditioner
bddc = LumpedBDDC(finediffusion);

# verify
println(bddc)
println(bddc.operator)

# output

lumped BDDC preconditioner
finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
operator field:
  tensor product basis:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 5
    numberquadraturepoints1d: 5
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
```
