```
Either{L, R} = Union{Const{L}, Identity{R}}
Either{Int, Bool}(true) == Identity(true)
Either{Int, Bool}(1) == Const(1)
Either{String}("left") == Const("left")
Either{String}(:anythingelse) == Identity(:anythingelse)
```

結果または失敗を表すための非常に一般的な型です。私たちは[`Identity`](@ref)を「成功」を表すために、[`Const`](@ref)を「失敗」を表すために再利用します。
