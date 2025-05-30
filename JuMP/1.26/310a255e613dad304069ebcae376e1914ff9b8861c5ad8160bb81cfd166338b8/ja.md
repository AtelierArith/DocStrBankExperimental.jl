```
VariableInSetRef(
    model::GenericModel,
    x::Union{AbstractJuMPScalar,AbstractArray{<:AbstractJuMPScalar}},
)
```

`x`が作成時に制約されている場合に関連付けられた制約参照を返します。

変数は、[`@variable`](@ref) マクロ内で `x in S` または `x, set = S` 構文を使用する場合に作成時に制約されます。

この関数は、`x`が作成時に制約されていなかった場合にエラーを返します。変数が作成時に制約されていたかどうかを確認するには、[`is_variable_in_set`](@ref) を使用してください。

## 例外

この関数は、スカラー変数の変数境界や整数制約には適用されません。例えば：

```jldoctest variable_in_set_ref_docstring
julia> model = Model();

julia> @variable(model, x >= 0, Int)
x

julia> is_variable_in_set(x)
false
```

代わりに、[`IntegerRef`](@ref)、[`BinaryRef`](@ref)、[`LowerBoundRef`](@ref)、[`UpperBoundRef`](@ref)、および [`FixRef`](@ref) を使用してください。

```jldoctest variable_in_set_ref_docstring
julia> model = Model();

julia> @variable(model, x >= 0, Int)
x

julia> IntegerRef(x)
x integer

julia> LowerBoundRef(x)
x ≥ 0
```

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2, 1:2], PSD)
2×2 LinearAlgebra.Symmetric{VariableRef, Matrix{VariableRef}}:
 x[1,1]  x[1,2]
 x[1,2]  x[2,2]

julia> is_variable_in_set(x)
true

julia> c = VariableInSetRef(x)
[x[1,1]  x[1,2]
 ⋯       x[2,2]] ∈ PSDCone()

julia> @variable(model, y)
y

julia> is_variable_in_set(y)
false

julia> @variable(model, z in Semicontinuous(1, 2))
z

julia> is_variable_in_set(z)
true

julia> c_z = VariableInSetRef(z)
z ∈ MathOptInterface.Semicontinuous{Int64}(1, 2)
```
