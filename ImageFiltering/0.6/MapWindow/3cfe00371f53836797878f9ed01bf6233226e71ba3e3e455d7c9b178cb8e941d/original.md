```
mapwindow!(f, out, img, window; border="replicate", indices=axes(img))
```

Variant of [mapwindow](@ref), with preallocated output. If `out` and `img` have overlapping memory regions, behaviour is undefined.
