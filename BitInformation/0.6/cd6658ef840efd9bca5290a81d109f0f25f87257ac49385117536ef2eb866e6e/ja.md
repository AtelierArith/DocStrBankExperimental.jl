```julia
B = biased_exponent(A::AbstractArray{T}) where {T<:Base.IEEEFloat}
```

符号付き指数を `signed_exponent` から IEEE 浮動小数点の標準バイアス指数に戻します。
