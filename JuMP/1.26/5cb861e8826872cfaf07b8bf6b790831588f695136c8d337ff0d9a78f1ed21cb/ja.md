```
operator_to_set(error_fn::Function, ::Val{sense_symbol})
```

感覚シンボルをセット `set` に変換します。これにより、`@constraint(model, func sense_symbol 0)` は任意の `func::AbstractJuMPScalar` に対して `@constraint(model, func in set)` と同等になります。

## 例

カスタムセットが定義されると、それを使用して直接JuMP制約を作成できます：

```jldoctest operator_to_set
julia> struct CustomSet{T} <: MOI.AbstractScalarSet
           value::T
       end

julia> Base.copy(x::CustomSet) = CustomSet(x.value)

julia> model = Model();

julia> @variable(model, x)
x

julia> cref = @constraint(model, x in CustomSet(1.0))
x ∈ CustomSet{Float64}(1.0)
```

ただし、より便利な構文を提供するために使用できる適切な記号があるかもしれません：

```jldoctest operator_to_set
julia> JuMP.operator_to_set(::Function, ::Val{:⊰}) = CustomSet(0.0)

julia> MOIU.supports_shift_constant(::Type{<:CustomSet}) = true

julia> MOIU.shift_constant(set::CustomSet, value) = CustomSet(set.value + value)

julia> cref = @constraint(model, x ⊰ 1)
x ∈ CustomSet{Float64}(1.0)
```

全体の関数はまず右辺に移動され、その後記号はゼロ定数のセットに変換され、最後に定数は `MOIU.shift_constant` を使用してセットに移動されることに注意してください。
