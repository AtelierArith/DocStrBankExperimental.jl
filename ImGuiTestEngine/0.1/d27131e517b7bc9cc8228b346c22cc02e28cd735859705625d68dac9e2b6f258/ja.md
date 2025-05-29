```julia
Start(
    engine::ImGuiTestEngine.Engine,
    ctx::Ptr{CImGui.lib.ImGuiContext}
)

```

テストエンジンコンテキストを開始します。CImGui.jlのレンダーループを使用している場合は、これを呼び出してはいけません。自動的に呼び出されます。

# 例

```julia
ctx = ig.CreateContext()
engine = te.CreateContext()
te.Start(engine, ctx)
```
