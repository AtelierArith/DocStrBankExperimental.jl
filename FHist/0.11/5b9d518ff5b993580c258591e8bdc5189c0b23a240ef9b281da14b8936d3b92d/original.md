```
project(h::Hist3D, axis::Symbol=:x)
project(axis::Symbol=:x) = h::Hist3D -> project(h, axis)
```

Computes the `:x`/`:y`/`:z` axis projection of the 3D histogram by summing over the specified axis. Returns a `Hist2D`.
