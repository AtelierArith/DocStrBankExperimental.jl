```
addmul!(a::AbstractLinear, b::AbstractLinear, c) -> a
addmul!(a::AbstractLinear, x, c) -> a
```

線形結合 `b` または項 `x` の `c` 倍を `a` に加えます。ここで、`c` はスカラーです。この関数は `a` を変更します。

関連項目として [`addmul`](@ref), [`add!`](@ref), [`sub!`](@ref), [`mul!`](@ref) を参照してください。
