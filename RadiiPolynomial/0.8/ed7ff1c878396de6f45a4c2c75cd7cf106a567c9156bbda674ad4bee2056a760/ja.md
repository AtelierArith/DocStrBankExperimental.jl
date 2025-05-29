```
banach_rounding_mul!(c::Sequence{<:SequenceSpace}, a::Sequence{<:SequenceSpace}, b::Sequence{<:SequenceSpace}, X::Ell1)
```

`project(banach_rounding_mul(a, b, X), space(c))` をインプレースで計算します。結果は `c` に上書きされて保存されます。

注意: `c` は `a` または `b` とエイリアスされてはいけません。

関連情報: [`banach_rounding_mul`](@ref), [`banach_rounding_pow`](@ref), [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref) および [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref).
