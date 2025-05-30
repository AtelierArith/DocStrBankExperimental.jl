```
normedview([T], img::AbstractArray{Unsigned})
```

は、`img`の「ビュー」を返し、値は`Normed`数値型として解釈されます。たとえば、`img`が`Array{UInt8}`の場合、ビューは`Array{N0f8}`のように動作します。`img`の要素型が`UInt16`の場合は、`T`を指定して、`N6f10`、`N4f12`、`N2f14`、または`N0f16`の結果を取得するかどうかを指定します。

参照: [`rawview`](@ref)
