```julia
GetKeyPressedAmount(
    key::CImGui.lib.ImGuiKey,
    repeat_delay,
    rate
) -> Int32

```

提供されたリピートレート/遅延を使用します。カウントを返し、最も一般的には0または1ですが、RepeatRateが小さくDeltaTime > RepeatRateの場合は1より大きくなることがあります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1004).
