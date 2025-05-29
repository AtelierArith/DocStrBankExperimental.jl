```
MutableUniformArray(val, args...) -> A
MutableUniformArray{T}(val, args...) -> A
MutableUniformArray{T,N}(val, args...) -> A
```

初期値がすべて `val` に等しい可変配列 `A` を作成し、軸は `args...` で指定します。 [`UniformArray`](@ref) のインスタンスとの違いは、均一な値を変更できることです。

`A[i] = x` のような文は、`A` のすべての要素の値を変更することができるため、`i` は `A` のすべてのインデックスを表す必要があります。変更できない均一配列を作成するには、[`UniformArray(val, dims)`](@ref) を呼び出してください。
