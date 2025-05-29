```
banach_rounding_pow(a::Sequence{<:SequenceSpace}, n::Int, X::Ell1)
```

`a`の離散畳み込み（`space(a)`に関連）を`n`回自分自身と計算します。このカットオフオーダーは、出力のこのオーダーを超える係数が厳密に囲まれるように推定されます。

参照: [`banach_rounding_mul`](@ref), [`banach_rounding_mul!`](@ref), [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref) および [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref).
