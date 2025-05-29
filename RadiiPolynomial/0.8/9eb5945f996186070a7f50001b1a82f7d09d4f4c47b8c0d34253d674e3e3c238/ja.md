```
(ℳ::Multiplication)(a::Sequence)
```

`sequence(ℳ)` と `a` の離散畳み込み（`space(sequence(ℳ))` と `space(a)` に関連する）を計算します。これは `sequence(ℳ) * a` と同等です。

参照: [`*(::Multiplication, ::Sequence)`](@ref), [`Multiplication`](@ref), [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref) および [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref).
