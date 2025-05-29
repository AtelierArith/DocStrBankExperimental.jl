```
set_normalized_coefficient(
    constraints::AbstractVector{
        <:ConstraintRef{<:AbstractModel,<:MOI.ConstraintIndex{F}},
    },
    variables::AbstractVector{<:AbstractVariableRef},
    coeffs::AbstractVector{<:Number},
) where {
    T,
    F<:Union{MOI.ScalarAffineFunction{T},MOI.ScalarQuadraticFunction{T}},
}
```

`constraints`の制約において`variables`の複数の係数を`coeffs`に設定します。

## 具体的な型

`constraints`は単一の制約タイプの具体的なベクターでなければなりません。例えば、`<=`と`>=`の制約を同じベクターに混在させることはできません。

## 正規化

このステップの前に、JuMPは同じ変数を含む複数の項を集約します。例えば、制約`2x + 3x <= 2`がある場合、`set_normalized_coefficient(con, [x], [4])`は制約`4x <= 2`を作成します。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, y)
y

julia> @constraint(model, con, 2x + 3x + 4y <= 2)
con : 5 x + 4 y ≤ 2

julia> set_normalized_coefficient([con, con], [x, y], [6, 7])

julia> con
con : 6 x + 7 y ≤ 2
```
