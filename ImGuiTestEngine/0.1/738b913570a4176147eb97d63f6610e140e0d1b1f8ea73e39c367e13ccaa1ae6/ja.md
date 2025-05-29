```julia
struct CxxPtr{ImGuiTestEngine.lib.ImGuiTestContext} <: CxxWrap.CxxWrapCore.CxxBaseRef{ImGuiTestEngine.lib.ImGuiTestContext}
```

これは `ImGuiTestContext` への参照です。直接作成することはできず、代わりにコンテキストは [`ImGuiTest`](@ref) の `GuiFunc` および `TestFunc` 関数に渡されます。

!!! danger
    これはメモリ安全でない型です。エンジンが生きている間だけ使用してください。

