```
smoptimize(f::Function, search_range::Array{Tuple{Float64,Float64},1}; options=Options())
```

ラジアル基底関数に基づくサロゲートモデルを使用して、範囲 `search_range` 内で関数 `f` を最適化します。
