```
precision(num::AbstractFloat; base::Integer=2)
precision(T::Type; base::Integer=2)
```

浮動小数点数の精度を取得します。これは、有効な桁数におけるビット数によって定義されます。また、浮動小数点型 `T` の精度（`T` が [`BigFloat`](@ref) のような可変精度型である場合はその現在のデフォルト）を取得します。

`base` が指定されている場合、その基数における最大の有効桁数を返します。

!!! compat "Julia 1.8"
    `base` キーワードは少なくとも Julia 1.8 が必要です。

