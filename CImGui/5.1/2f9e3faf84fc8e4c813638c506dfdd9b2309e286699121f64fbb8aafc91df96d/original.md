```julia
PushTextWrapPos()
PushTextWrapPos(wrap_local_pos_x)

```

Push word-wrapping position for Text*() commands. < 0.0f: no wrapping; 0.0f: wrap to end of window (or column); > 0.0f: wrap at 'wrap*pos*x' position in window local space.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L470).
