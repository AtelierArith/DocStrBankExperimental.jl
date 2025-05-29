```
Bits{T} <: AbstractArray{Bool,1}
```

可変の静的サイズのビットベクターで、型 `T <: Integer` の要素のビットにエンコードされています。

`Bits` は `BitVector` と似た動作をするべきですが、サイズがコンパイル時に `bitsize(T)` であることが知られているため、わずかに高速です。
