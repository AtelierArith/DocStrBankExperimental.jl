```
frommandel(S::Type{<: Union{SymmetricSecondOrderTensor, SymmetricFourthOrderTensor}}, A::AbstractArray{T})
```

Mandel形式からタイプ`S`のテンソルを作成します。これは`fromvoigt(S, A, offdiagscale = √2)`と同等です。

参照してください [`fromvoigt`](@ref)。
