```julia
FindViewportByPlatformHandle(
    platform_handle
) -> Ptr{CImGui.lib.ImGuiViewport}

```

これはバックエンド用のヘルパーです。型platform_handleはバックエンドによって決定されます（例：HWND、MyWindow*、GLFWwindow*など）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1097).
