```
mul!(c::Sequence{<:SequenceSpace}, a::Sequence{<:SequenceSpace}, b::Sequence{<:SequenceSpace}, α::Number, β::Number)
```

`project(a * b, space(c)) * α + c * β` をインプレースで計算します。結果は `c` に上書きされて保存されます。

注意: `c` は `a` または `b` のいずれともエイリアスであってはなりません。

参照: [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref), [`banach_rounding_mul`](@ref), [`banach_rounding_mul!`](@ref) および [`banach_rounding_pow`](@ref)。
