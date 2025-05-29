```julia
SetNextFrameWantCaptureKeyboard(want_capture_keyboard)

```

Override io.WantCaptureKeyboard flag next frame (said flag is left for your application to handle, typically when true it instructs your app to ignore inputs). e.g. force capture keyboard when your widget is being hovered. This is equivalent to setting "io.WantCaptureKeyboard = want*capture*keyboard"; after the next NewFrame() call.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1006).
