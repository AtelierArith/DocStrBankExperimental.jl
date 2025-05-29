```
banach_rounding_mul(a::Sequence{<:SequenceSpace}, b::Sequence{<:SequenceSpace}, X::Ell1)
```

`a` と `b` の離散畳み込み（`space(a)` と `space(b)` に関連付けられた）を計算します。出力の係数がこの順序を超える場合、厳密に囲まれるようにカットオフ順序が推定されます。

参照: [`banach_rounding_mul!`](@ref), [`banach_rounding_pow`](@ref), [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref) および [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref).
