```
function JuMP.build_constraint(
    _error::Function, 
    func::AbstractVector{T},
    set::S
) where {T <: Union{LogicalVariableRef, _LogicalExpr}, S <: Union{Exactly, AtLeast, AtMost}}
```

Extend `JuMP.build_constraint` to add logical cardinality constraints to a [`GDPModel`](@ref).  This in combination with `JuMP.add_constraint` enables the use of  `@constraint(model, [name], logical_expr in set)`, where set can be either of the following cardinality sets: `AtLeast(n)`, `AtMost(n)`, or `Exactly(n)`.

## Example

To select exactly 1 logical variable `Y` to be `true`, do  (the same can be done with `AtLeast(n)` and `AtMost(n)`):

```julia
using DisjunctiveProgramming
model = GDPModel();
@variable(model, Y[i = 1:2], LogicalVariable);
@constraint(model, [Y[1], Y[2]] in Exactly(1));
```
