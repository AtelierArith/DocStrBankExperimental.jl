```
div_with_overflow(x::FixedDecimal{T,f}, y::FixedDecimal{T,f})::(FixedDecimal{T,f}, Bool)
    where {T<:Integer, f}
```

ゼロ除算の場合は DivideError をスローします。オーバーフロー/アンダーフローが実際に発生したかどうかを示すブール値とともに、（オーバーフロー/アンダーフローでラッピングされた）div の結果を返します。
