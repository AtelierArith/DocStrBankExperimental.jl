```
 getindex(surf, s, Inclusive())
```

Access supplementary spatial data `s::Symbol` for a `SurfaceSpace`. Optionally pass  a `MedialWallIndexing` trait `Inclusive()` or `Exclusive()` to inform handling  of medial wall (default is `Inclusive()`).
