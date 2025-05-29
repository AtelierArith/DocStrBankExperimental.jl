```
jump_function(model::AbstractModel, x::MOI.AbstractFunction)
```

MathOptInterfaceオブジェクト`x`を与えると、JuMPの同等のものを返します。

参照: [`moi_function`](@ref)。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> f = 2.0 * index(x) + 1.0
1.0 + 2.0 MOI.VariableIndex(1)

julia> jump_function(model, f)
2 x + 1
```
