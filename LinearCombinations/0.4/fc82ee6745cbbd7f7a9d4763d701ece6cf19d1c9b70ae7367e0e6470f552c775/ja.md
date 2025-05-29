```
add!(a::AbstractLinear, b::AbstractLinear) -> a
add!(a::AbstractLinear, x) -> a
```

線形結合 `b` または項 `x` を `a` に追加します。この関数は `a` を変更します。

関連情報として [`addmul!`](@ref)、[`sub!`](@ref) を参照してください。
