```
project(h::Hist2D, axis::Symbol=:x)
project(axis::Symbol=:x) = h::Hist2D -> project(h, axis)
```

Computes the `:x` (`:y`) axis projection of the 2D histogram by summing over the y (x) axis. Returns a `Hist1D`.
