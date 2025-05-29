```julia
GalleryVectorOperator(name, numbernodes1d, numberquadraturepoints1d, numberelements1d, mesh)
```

Finite element operator from a gallery of options

# Arguments:

  * `name::String`:                   string containing name of operator
  * `numbernodes1d::Int`:             polynomial order of TensorH1LagrangeBasis
  * `numberquadraturepoints1d::Int`:  number of quadrature points in one dimension for basis
  * `numbercomponents::Int`:          number of components
  * `mesh::Mesh`:                     mesh for operator

# Returns:

  * finite element operator object

# Mass matrix example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryVectorOperator("mass", 4, 4, 3, mesh);

# verify
println(mass)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    interpolation
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    interpolation
```

# Diffusion operator example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
diffusion = GalleryVectorOperator("diffusion", 4, 4, 3, mesh);

# verify
println(diffusion)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    gradient
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 3
    dimension: 2
  evaluation mode:
    gradient
```
