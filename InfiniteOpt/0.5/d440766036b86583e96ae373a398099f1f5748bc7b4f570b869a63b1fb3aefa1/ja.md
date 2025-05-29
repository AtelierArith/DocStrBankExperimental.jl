```
build_derivative(_error::Function, info::JuMP.VariableInfo, 
                 argument_ref::GeneralVariableRef, 
                 parameter_ref::GeneralVariableRef
                 )::Derivative
```

`parameter_ref` に依存し、`argument_ref` に作用する微分演算子を持つ [`Derivative`](@ref) を構築して返します。変数 `info` を提供することで、この微分を無限変数のように境界や開始値関数に関連付けることもできます。`argument_ref` が無限/半無限変数でない場合や、`parameter_ref` に依存する微分でない場合にエラーが発生します。

**例** ```julia-repl  julia> @infinite*parameter(m, t in [0, 1]); @infinite*variable(m, x(t));

julia> info = VariableInfo(false, 0, false, 0, false, 0, false, 0, false, false);

julia> build*derivative(error, info, x, t) Derivative{GeneralVariableRef}(VariableInfo{Float64,Float64,Float64,Function}(false, 0.0, false, 0.0, false, 0.0, false, start*func, false, false), true, x(t), t) ````
