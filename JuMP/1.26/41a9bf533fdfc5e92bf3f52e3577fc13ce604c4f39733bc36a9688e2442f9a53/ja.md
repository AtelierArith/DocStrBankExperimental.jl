```
moi_function_type(::Type{T}) where {T}
```

JuMPオブジェクトタイプ`T`に対して、MathOptInterfaceの同等のものを返します。

参照: [`jump_function_type`](@ref)。

## 例

```jldoctest
julia> moi_function_type(AffExpr)
MathOptInterface.ScalarAffineFunction{Float64}
```
