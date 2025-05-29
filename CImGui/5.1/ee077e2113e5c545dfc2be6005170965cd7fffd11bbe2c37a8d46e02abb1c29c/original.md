```julia
SetColorEditOptions(
    flags::Union{CImGui.lib.ImGuiColorEditFlags_, Integer}
)

```

Initialize current options (generally on application startup) if you want to select a default format, picker type, etc. User will be able to change many settings, unless you pass the _NoOptions flag to your calls.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L663).
