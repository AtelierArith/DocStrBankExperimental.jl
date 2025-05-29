```julia
GalleryOperator(
    name,
    numbernodes1d,
    numberquadraturepoints1d,
    mesh;
    collocatedquadrature = false,
    mapping = nothing,
    parameters = nothing,
)
```

Finite element operator from a gallery of options

# Arguments:

  * `name::String`:                   string containing name of operator
  * `numbernodes1d::Int`:             polynomial order of TensorH1LagrangeBasis
  * `numberquadraturepoints1d::Int`:  number of quadrature points in one dimension for basis
  * `mesh::Mesh`:                     mesh for operator

# Keyword Arguments:

  * `collocatedquadrature::Bool = false`:                        Gauss-Legendre or Gauss-Legendre-Lobatto quadrature points
  * `mappingUnion{Tuple{Function,Function},Nothing} = nothing`:  quadrature point mapping - sausage, Kosloff-Talezer, Hale-Trefethen strip, or no transformation
  * `parametersUnion{NamedTuple,Nothing} = nothing`:             named tuple of model parameters

# Returns:

  * finite element operator object

# Mass matrix example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
mass = GalleryOperator("mass", 4, 4, mesh);

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
    interpolation
```

# Diffusion operator example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
diffusion = GalleryOperator("diffusion", 4, 4, mesh);

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
    numbercomponents: 1
    dimension: 2
  evaluation mode:
    gradient
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

# Advection operator example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
advection = GalleryOperator("advection", 4, 4, mesh);

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

# SUPG mass matrix example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
parameters = (wind = [1.0, 1.0], τ = 1.0);
supgmass = GalleryOperator("supg mass", 4, 4, mesh, parameters = parameters);

# verify
println(supgmass)

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
  evaluation modes:
    interpolation
    gradient
```

# SUPG advection operator example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
parameters = nothing;
supgadvection = GalleryOperator("supg advection", 4, 4, mesh, parameters = parameters);

# verify
println(supgadvection)

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
  evaluation modes:
    interpolation
    gradient
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
