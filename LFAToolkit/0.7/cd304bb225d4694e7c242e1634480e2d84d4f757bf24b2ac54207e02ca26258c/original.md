```julia
GalleryMacroElementOperator(
    name,
    numbernodes1d,
    numberquadraturepoints1d,
    numberelements1d,
    mesh;
    mapping = nothing,
    parameters = nothing,
)
```

Finite element operator from a gallery of options

# Arguments:

  * `name::String`:                   string containing name of operator
  * `numbernodes1d::Int`:             polynomial order of TensorH1LagrangeBasis
  * `numberquadraturepoints1d::Int`:  number of quadrature points in one dimension for basis
  * `numberelements1d::Int`:          number of elements in macro-element
  * `mesh::Mesh`:                     mesh for operator

# Keyword Arguments:

  * `mapping::Union{Tuple{Function,Function},Nothing} = nothing`:  quadrature point mapping - sausage, Kosloff-Talezer, Hale-Trefethen strip, or no transformation
  * `parameters::Union{NamedTuple,Nothing}` = nothing:             named tuple of model parameters

# Returns:

  * finite element operator object

# Mass matrix example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryMacroElementOperator("mass", 4, 4, 2, mesh);

# verify
println(mass)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    interpolation
operator field:
  macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    interpolation
```

# Diffusion operator example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
diffusion = GalleryMacroElementOperator("diffusion", 4, 4, 2, mesh);

# verify
println(diffusion)

# output

finite element operator:
2d mesh:
    dx: 1.0
    dy: 1.0

2 inputs:
operator field:
  macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    gradient
operator field:
  macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  macro-element tensor product basis:
    numbernodes1d: 7
    numberquadraturepoints1d: 8
    numbercomponents: 1
    numberelements1d: 2
    dimension: 2
  evaluation mode:
    gradient
```

# Advection operator example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
advection = GalleryVectorOperator("advection", 4, 4, 1, mesh);

# verify
println(advection)

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
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    interpolation
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    quadratureweights

1 output:
operator field:
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 4
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
```
