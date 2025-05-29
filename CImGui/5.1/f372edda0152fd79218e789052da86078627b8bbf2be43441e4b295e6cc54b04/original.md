```julia
FindViewportByPlatformHandle(
    platform_handle
) -> Ptr{CImGui.lib.ImGuiViewport}

```

This is a helper for backends. the type platform_handle is decided by the backend (e.g. HWND, MyWindow*, GLFWwindow* etc.).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1097).
