```
fnv1(T, p::Ptr{UInt8}, n::Integer)
fnv1(T, x::Union{String, DenseVector{UInt8}})
```

入力のFowler-Noll-Voバージョン1ハッシュを、Tで定義されたビット幅に対して計算します。Tは符号なしでなければなりません。
