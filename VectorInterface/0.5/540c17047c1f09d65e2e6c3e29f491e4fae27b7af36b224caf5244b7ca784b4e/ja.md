```
scale!(x, α::Number) -> x
scale!(y, x, α::Number) -> y
```

スケール係数 `α` を用いて `x` を再スケールし、これにより `x` の内容を上書きして再利用します（最初の形式の場合）または `y` の内容を上書きします（2 番目の形式の場合）。これは、`x` または `y` が可変であり、関与するスカラー型が互換性があり、昇格および変換できる場合にのみ可能です。

また、[`scale`](@ref) および [`scale!!`](@ref) も参照してください。
