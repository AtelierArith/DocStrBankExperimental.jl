```
build_derivative(_error::Function, info::JuMP.VariableInfo, 
                 argument_ref::GeneralVariableRef, 
                 parameter_ref::GeneralVariableRef
                 )::Derivative
```

Constructs and returns a [`Derivative`](@ref) with a differential operator that  depends on `parameter_ref` and operates on `argument_ref`. Variable `info` can also  be provided to associate this derivative with bounds and a starting value function  like that of infinite variables. Errors when `argument_ref` is not an  infinite/semi-infinite variable or derivative that depends on `parameter_ref`.

**Example** ```julia-repl  julia> @infinite*parameter(m, t in [0, 1]); @infinite*variable(m, x(t));

julia> info = VariableInfo(false, 0, false, 0, false, 0, false, 0, false, false);

julia> build*derivative(error, info, x, t) Derivative{GeneralVariableRef}(VariableInfo{Float64,Float64,Float64,Function}(false, 0.0, false, 0.0, false, 0.0, false, start*func, false, false), true, x(t), t) ````
