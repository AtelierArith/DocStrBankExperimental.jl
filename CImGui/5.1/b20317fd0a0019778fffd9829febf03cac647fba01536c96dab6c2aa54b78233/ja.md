```julia
IsBuilt(self::Ptr{CImGui.lib.ImFontAtlas}) -> Bool

```

少しあいまいです：ユーザーがテクスチャをビルドしなかったときに検出するために使用されますが、実際にはTexID != 0をチェックする必要があります。ただし、それはバックエンドに依存します...

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L3485).
