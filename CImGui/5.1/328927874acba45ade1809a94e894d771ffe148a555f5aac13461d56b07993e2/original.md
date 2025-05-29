```julia
TextWrapped(fmt)

```

Shortcut for PushTextWrapPos(0.0f); Text(fmt, ...); PopTextWrapPos();. Note that this won't work on an auto-resizing window if there's no other widgets to extend the window width, yoy may need to set a size using SetNextWindowSize().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L549).
