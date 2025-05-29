```
Evaluation{T<:Union{Nothing,Number,Tuple{Vararg{Union{Nothing,Number}}}}} <: SpecialOperator
```

汎用評価演算子。`nothing`の値は、評価を行わないことを示します。

フィールド:

  * `value :: T`

コンストラクタ:

  * `Evaluation(::Union{Nothing,Number})`
  * `Evaluation(::Tuple{Vararg{Union{Nothing,Number}}})`
  * `Evaluation(value::Union{Number,Nothing}...)`: `Evaluation(value)`と同等です。

参照: [`evaluate`](@ref), [`evaluate!`](@ref), [`project(::Evaluation, ::VectorSpace, ::VectorSpace)`](@ref) および [`project!(::LinearOperator, ::Evaluation)`](@ref)。

# 例

```jldoctest
julia> Evaluation(1.0)
Evaluation{Float64}(1.0)

julia> Evaluation(1.0, nothing, 2.0)
Evaluation{Tuple{Float64, Nothing, Float64}}((1.0, nothing, 2.0))
```
