```
H = bitcount_entropy(A::AbstractArray{T},base::Real=2) where {T<:Union{Integer,AbstractFloat}}
```

`H`は、`A`の要素における`T`の各ビット位置での0と1の出現に対するエントロピーのベクトルを返します。`bitcount`関数を利用し、0ビットと1ビットの確率からエントロピーを計算します。基数`base`はデフォルトで2であり、エントロピーの単位はビットです。
