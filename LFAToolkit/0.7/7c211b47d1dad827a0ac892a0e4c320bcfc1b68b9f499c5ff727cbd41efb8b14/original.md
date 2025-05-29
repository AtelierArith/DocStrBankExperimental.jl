```julia
Operator(weakform, mesh, inputs, outputs)
```

Finite element operator comprising of a weak form and bases

# Arguments:

  * `weakform::Function`:                     user provided function that represents weak form at quadrature points
  * `mesh::Mesh`:                             mesh object with deformation in each dimension
  * `inputs::AbstractArray{OperatorField}`:   array of operator input fields
  * `outputs::AbstractArray{OperatorField}`:  array of operator output fields

# Returns:

  * finite element operator object

# Example:

```jldoctest
# setup
mesh = Mesh2D(1.0, 1.0);
basis = TensorH1LagrangeBasis(4, 4, 1, 2);

function massweakform(u::Array{Float64}, w::Array{Float64})
    v = u * w[1]
    return [v]
end

# mass operator
inputs = [
    OperatorField(basis, [EvaluationMode.interpolation]),
    OperatorField(basis, [EvaluationMode.quadratureweights]),
];
outputs = [OperatorField(basis, [EvaluationMode.interpolation])];
mass = Operator(massweakform, mesh, inputs, outputs);

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
