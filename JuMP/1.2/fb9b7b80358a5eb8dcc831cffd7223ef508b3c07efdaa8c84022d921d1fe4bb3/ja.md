```
objective_function(model::Model,
               T::Type{<:AbstractJuMPScalar}=objective_function_type(model))
```

目的関数を表す型 `T` のオブジェクトを返します。目的が型 `T` に変換できない場合はエラーになります。

## 例

```jldoctest objective_function; setup = :(using JuMP)
julia> model = Model()
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.

julia> @variable(model, x)
x

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> objective_function(model, AffExpr)
2 x + 1

julia> objective_function(model, QuadExpr)
2 x + 1

julia> typeof(objective_function(model, QuadExpr))
GenericQuadExpr{Float64,VariableRef}
```

最後の2つのコマンドからわかるように、目的関数がアフィンであっても、二次関数に変換可能であれば、二次関数としてクエリでき、その結果は二次関数になります。

しかし、変数に変換することはできません。

```jldoctest objective_function; filter = r"MathOptInterface\."s
julia> objective_function(model, VariableRef)
ERROR: InexactError: convert(MathOptInterface.VariableIndex, MathOptInterface.ScalarAffineFunction{Float64}(MathOptInterface.ScalarAffineTerm{Float64}[MathOptInterface.ScalarAffineTerm{Float64}(2.0, MathOptInterface.VariableIndex(1))], 1.0))
[...]
```
