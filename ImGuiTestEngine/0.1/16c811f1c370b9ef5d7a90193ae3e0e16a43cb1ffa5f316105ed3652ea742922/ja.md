```julia
QueueTest(
    engine::ImGuiTestEngine.Engine,
    test::ImGuiTestEngine.ImGuiTest
)
QueueTest(
    engine::ImGuiTestEngine.Engine,
    test::ImGuiTestEngine.ImGuiTest,
    run_flags
)

```

特定のテストを実行のためにキューに追加します。CImGui.jlのレンダーループを使用している場合、これを自分で呼び出す必要はありません。

# 例

```julia
engine = te.CreateContext()
t = @register_test(engine, "foo", "bar") do ctx
    @info "Hello world!"
end

te.QueueTest(engine, t)
```
