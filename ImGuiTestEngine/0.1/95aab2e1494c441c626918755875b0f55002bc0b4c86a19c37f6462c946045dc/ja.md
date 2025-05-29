```julia
Stop(engine::ImGuiTestEngine.Engine)

```

テストエンジンコンテキストを停止します。

# 例

```julia
ctx = ig.CreateContext()
engine = te.CreateContext()
te.Start(engine, ctx)
te.Stop(engine)
```
