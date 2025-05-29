```
FastUniformArray(val, args...) -> A
FastUniformArray{T}(val, args...) -> A
FastUniformArray{T,N}(val, args...) -> A
FastUniformArray{T,N,val}(args...) -> A
```

不変の均一配列 `A` を構築し、その要素はすべて `val` に等しく、軸は `args...` で指定されます。 [`UniformArray`](@ref) のインスタンスとの違いは、`val` が型シグネチャの一部であるため、`val` をコンパイル時に知ることができる点です。典型的な使用法は、すべての真/偽マスクを作成することです。
