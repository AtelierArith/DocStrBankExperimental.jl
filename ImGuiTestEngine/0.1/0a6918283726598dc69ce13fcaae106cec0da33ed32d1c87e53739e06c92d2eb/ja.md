```
@register_test(engine, category::AbstractString, name::AbstractString)::ImGuiTest
@register_test(f::Function, engine,
               category::AbstractString, name::AbstractString)::ImGuiTest
```

[`ImGuiTest`](@ref)を登録します。テストは、プログラム的に[`QueueTests()`](@ref)を使用するか、ユーザーが手動で[`ShowTestEngineWindows()`](@ref)を実行するまで実行されないことに注意してください。

# 例

`TestFunc`だけを設定する必要がある場合は、do構文を使用できます：

```julia
engine = te.CreateContext()
@register_test(engine, "foo", "bar") do ctx
    @imtest ctx isa te.TestContext
end
```

`GuiFunc`も設定する必要がある場合は、`GuiFunc`プロパティを設定する必要があります：

```julia
engine = te.CreateContext()
t = @register_test(engine, "foo", "bar")
t.GuiFunc = ctx -> begin
    ig.Begin("Foo")
    ig.End()
end
t.TestFunc = ctx -> @info "Hello world!"
```
