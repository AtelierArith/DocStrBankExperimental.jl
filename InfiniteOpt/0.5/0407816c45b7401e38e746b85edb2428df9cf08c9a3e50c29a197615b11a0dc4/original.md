```
JuMP.constraint_object(cref::InfOptConstraintRef)::JuMP.AbstractConstraint
```

Extend `JuMP.constraint_object` to return the constraint object associated with  `cref`.

**Example**

```julia-repl
julia> @infinite_parameter(model, t in [0, 10]);

julia> @variable(model, x <= 1);

julia> cref = UpperBoundRef(x);

julia> obj = constraint_object(cref)
ScalarConstraint{GeneralVariableRef,MathOptInterface.LessThan{Float64}}(x,
MathOptInterface.LessThan{Float64}(1.0))
```
