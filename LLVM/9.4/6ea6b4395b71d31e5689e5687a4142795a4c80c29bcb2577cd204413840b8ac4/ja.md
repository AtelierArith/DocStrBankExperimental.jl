```
convert(::Type{<:AbstractFloat}, val::GenericValue, typ::LLVM.FloatingPointType)
```

汎用値を指定された型の浮動小数点数に変換します。

整数変換とは異なり、LLVM型も明示的に渡す必要があります。
