```
ceil([T,] x)
ceil(x; digits::Integer= [, base = 10])
ceil(x; sigdigits::Integer= [, base = 10])
```

`ceil(x)` は、`x` 以上の同じ型の最も近い整数値を返します。

`ceil(T, x)` は結果を型 `T` に変換し、値が表現できない場合は `InexactError` をスローします。

キーワード `digits`、`sigdigits` および `base` は [`round`](@ref) と同様に機能します。
