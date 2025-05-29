```julia
SetNextFrameWantCaptureMouse(want_capture_mouse)

```

Override io.WantCaptureMouse flag next frame (said flag is left for your application to handle, typical when true it instucts your app to ignore inputs). This is equivalent to setting "io.WantCaptureMouse = want*capture*mouse;" after the next NewFrame() call.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1054).
