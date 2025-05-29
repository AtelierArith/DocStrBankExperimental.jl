```julia
EndFrame()

```

Dear ImGuiフレームを終了します。Render()によって自動的に呼び出されます。データをレンダリングする必要がない場合（レンダリングをスキップする場合）、Render()なしでEndFrame()を呼び出すことができますが、すでにCPUを無駄にしてしまったことになります！レンダリングが必要ない場合は、ウィンドウを作成せず、NewFrame()を全く呼び出さない方が良いでしょう。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L344).
