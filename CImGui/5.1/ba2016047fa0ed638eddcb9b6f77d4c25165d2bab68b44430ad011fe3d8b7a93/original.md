```julia
IsWindowHovered() -> Bool
IsWindowHovered(
    flags::Union{CImGui.lib.ImGuiHoveredFlags_, Integer}
) -> Bool

```

Is current window hovered and hoverable (e.g. not blocked by a popup/modal)? See ImGuiHoveredFlags_ for options. IMPORTANT: If you are trying to check whether your mouse should be dispatched to Dear ImGui or to your underlying app, you should not use this function! Use the 'io.WantCaptureMouse' boolean for that! Refer to FAQ entry "How can I tell whether to dispatch mouse/keyboard to Dear ImGui or my application?" for details.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L407).
