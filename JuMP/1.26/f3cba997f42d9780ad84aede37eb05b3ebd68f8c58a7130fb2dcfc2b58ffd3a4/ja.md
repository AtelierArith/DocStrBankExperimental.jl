```
jump_function_type(model::AbstractModel, ::Type{T}) where {T}
```

MathOptInterfaceオブジェクトタイプ`T`を指定すると、JuMPの同等のものを返します。

参照: [`moi_function_type`](@ref)。

## 例

```jldoctest
julia> model = Model();

julia> jump_function_type(model, MOI.ScalarAffineFunction{Float64})
AffExpr (alias for GenericAffExpr{Float64, GenericVariableRef{Float64}})
```
