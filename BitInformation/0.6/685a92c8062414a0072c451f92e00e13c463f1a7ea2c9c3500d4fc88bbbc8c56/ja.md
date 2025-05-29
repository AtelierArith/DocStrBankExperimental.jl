```
C = bitcount(A::AbstractArray{T}) where {T<:Union{Integer,AbstractFloat}}
```

`A`のすべての要素にわたる各ビット位置での1ビットの出現回数をカウントします。最初のエントリが型`T`の要素の最初のビットを表すカウンター配列`C::Vector{Int}`を返します。例えば、浮動小数点数の場合は符号ビットです。
