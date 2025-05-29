```julia
QueueTests(engine::ImGuiTestEngine.Engine)
QueueTests(
    engine::ImGuiTestEngine.Engine,
    group::ImGuiTestEngine.TestGroup
)
QueueTests(
    engine::ImGuiTestEngine.Engine,
    group::ImGuiTestEngine.TestGroup,
    filter
)
QueueTests(
    engine::ImGuiTestEngine.Engine,
    group::ImGuiTestEngine.TestGroup,
    filter,
    run_flags
)

```

特定のグループ内のすべてのテストをキューに追加します。CImGui.jlのレンダーループを使用している場合は、自分でこれを呼び出す必要はありません。

# 例

```julia
engine = te.CreateContext()
t = @register_test(engine, "foo", "bar") do ctx
    @info "Hello world!"
end

# すべてのテストをキューに追加
te.QueueTests(engine)
```
