```
support_sum(expr::JuMP.AbstractJuMPScalar,
            params::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}};
            label = All
            )::GeneralVariableRef
```

パラメータに対する式の合計を、その `label` に対応するすべてのサポートを使用して表す測度を作成します。また、`expr` が単一の変数参照でない場合は、[`@support_sum`](@ref) を呼び出すことが推奨されます。

**例**

```julia-repl
julia> @infinite_parameter(model, x in [0, 1], supports = [0.3, 0.7])
x

julia> @variable(model, f, Infinite(x))
f(x)

julia> meas = support_sum(f, x)
support_sum{x}[f(x)]

julia> expand(meas)
f(0.3) + f(0.7)
```
