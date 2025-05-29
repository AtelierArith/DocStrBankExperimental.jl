```julia
IsMouseReleasedWithDelay(
    button::Union{CImGui.lib.ImGuiMouseButton_, Integer},
    delay
) -> Bool

```

Delayed mouse release (use very sparingly!). Generally used with 'delay >= io.MouseDoubleClickTime' + combined with a 'io.MouseClickedLastCount==1' test. This is a very rarely used UI idiom, but some apps use this: e.g. MS Explorer single click on an icon to rename.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1042).
