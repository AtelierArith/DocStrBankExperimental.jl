```
function FEEvaluator(FE::FESpace, operator::AbstractFunctionOperator, qrule::QuadratureRule; T = Float64, AT = ON_CELLS, L2G = nothing)
```

Constructs a FEEvaluator that handles evaluations of finite element basis function evaluation for the given FESpace, operator at the quadrature points of the given QuadratureRule. It has an update! function to update the evaluation upon entry to a new cell. Evaluations can be accessed via FEEvaluator.cvals[j,k,i] where i is the quadrature point id, k is the local dof number and j is the component. 

Note that matrix-valued operators evaluations, e.g. for Gradient, are given as a long vector (in component-wise order).
