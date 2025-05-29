```julia
mutable struct Engine
```

テストエンジンコンテキストを表します。これは、上流の `ImGuiTestEngine` 型のラッパーです。自分で作成しないでください、[`CreateContext()`](@ref) を使用してください。
