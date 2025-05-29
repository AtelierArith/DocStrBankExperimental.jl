```julia
GetKeyPressedAmount(
    key::CImGui.lib.ImGuiKey,
    repeat_delay,
    rate
) -> Int32

```

Uses provided repeat rate/delay. return a count, most often 0 or 1 but might be >1 if RepeatRate is small enough that DeltaTime > RepeatRate.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1004).
