```julia
AddDrawCmd(self::Ptr{CImGui.lib.ImDrawList})

```

これは、依存レンダリング/ブレンディングを可能にするために、新しい描画コールを強制的に作成する必要がある場合に便利です。そうでなければ、プリミティブは可能な限り同じ描画コールに統合されます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3290).
