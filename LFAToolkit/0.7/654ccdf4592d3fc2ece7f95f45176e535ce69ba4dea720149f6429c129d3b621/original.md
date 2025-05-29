```julia
OperatorField(basis, evaluationmodes)
```

Finite Element operator input or output, with a basis and evaluation mode

# Arguments:

  * `basis::AbstractBasis`:                           finite element basis for the field
  * `evaluationmodes::AbstractArray{EvaluationMode`:  array of basis evaluation modes; note: quadrature weights must be listed in a separate operator field

# Optional Agrument:

  * `name::String`:  name of operator field

# Returns:

  * finite element operator field object

# Example:

```jldoctest
# basis
basis = TensorH1LagrangeBasis(4, 3, 2, 1);

# quadrature weights field, input only
weightsfield =
    OperatorField(basis, [EvaluationMode.quadratureweights], "quadrature weights");

# verify
println(weightsfield)

# input or output field
inputfield = OperatorField(
    basis,
    [EvaluationMode.interpolation, EvaluationMode.gradient],
    "gradient of weak form input",
);

# verify
println(inputfield)

# output

operator field:
  name:
    quadrature weights 
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 3
    numbercomponents: 2
    dimension: 1
  evaluation mode:
    quadratureweights
operator field:
  name:
    gradient of weak form input
  tensor product basis:
    numbernodes1d: 4
    numberquadraturepoints1d: 3
    numbercomponents: 2
    dimension: 1
  evaluation modes:
    interpolation
    gradient
```
