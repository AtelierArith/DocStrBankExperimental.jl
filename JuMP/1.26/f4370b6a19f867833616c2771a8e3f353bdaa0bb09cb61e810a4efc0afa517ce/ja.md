```
moi_function(x::AbstractJuMPScalar)
moi_function(x::AbstractArray{<:AbstractJuMPScalar})
```

JuMPオブジェクト`x`を与えると、MathOptInterfaceの同等のものを返します。

参照: [`jump_function`](@ref)。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> f = 2.0 * x + 1.0
2 x + 1

julia> moi_function(f)
1.0 + 2.0 MOI.VariableIndex(1)
```
