```
sub!(a::AbstractLinear, b::AbstractLinear) -> a
sub!(a::AbstractLinear, x) -> a
```

線形結合 `b` または項 `x` を `a` から引きます。この関数は `a` を変更します。

関連項目として [`addmul!`](@ref)、[`add!`](@ref) を参照してください。
