```
num_components(::Type{<:Number})
num_components(a::Number)
```

`Number` または `MultiValue` のコンポーネントの総数、すなわちスカラーの場合は 1 であり、`MultiValue` の場合はサイズの次元の積です。これは `length` と同じです。
