```julia
IsItemToggledSelection() -> Bool

```

Was the last item selection state toggled? Useful if you need the per-item information *before* reaching EndMultiSelect(). We only returns toggle *event* in order to handle clipping correctly.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L702).
