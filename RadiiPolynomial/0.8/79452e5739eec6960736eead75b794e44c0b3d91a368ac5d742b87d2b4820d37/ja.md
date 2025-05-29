```
Multiplication{T<:Sequence{<:SequenceSpace}} <: SpecialOperator
```

与えられた [`Sequence`](@ref) に関連付けられた乗算演算子。

フィールド:

  * `sequence :: T`

コンストラクタ:

  * `Multiplication(::Sequence{<:SequenceSpace})`

参照:

  * [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref), [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref), [`project(::Multiplication, ::SequenceSpace, ::SequenceSpace)`](@ref), [`project!(::LinearOperator{<:SequenceSpace,<:SequenceSpace}, ::Multiplication)`](@ref) および [`Multiplication`](@ref).
