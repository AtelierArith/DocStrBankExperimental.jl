```julia
DeIndexAllBuffers(self::Ptr{CImGui.lib.ImDrawData})

```

インデックス付きでレンダリングできない場合に備えて、すべてのバッファをインデックスなしに変換するためのヘルパーです。注意: これは遅く、リソースの無駄になる可能性が高いです。常にインデックス付きレンダリングを優先してください！

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3355).
