```
fnv1a(T, p::Ptr{UInt8}, n::Integer)
fnv1a(T, x::Union{String, DenseVector{UInt8}})
```

入力のFowler-Noll-Voバージョン1aハッシュを、Tで定義されたビット幅に対して計算します。Tは符号なしでなければなりません。
