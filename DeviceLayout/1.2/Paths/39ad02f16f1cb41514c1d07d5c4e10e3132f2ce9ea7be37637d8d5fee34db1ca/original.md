```
overlay!(path::Path, oversty::Style, metadata::DeviceLayout.Meta; i::Int=length(path))
```

Apply the style `oversty` in layer `metadata` on top of the segment at `path[i]`.

By default, the overlay is applied to the most recent segment.

Overlays generally count as "decorations". For example, they appear in `refs(path)` and not `elements(path)`. They are removed by `undecorated(sty)`, and they are ignored when choosing the default style for continuing a `Path` with methods like `straight!`.

Overlay styles should not be generic `Paths.Taper`s, since they can't see neighboring styles to resolve the taper style.

You can use `overlay!` after `attach!`, in which case the overlay is applied to the style underlying the `DecoratedStyle` that holds the attachments.
