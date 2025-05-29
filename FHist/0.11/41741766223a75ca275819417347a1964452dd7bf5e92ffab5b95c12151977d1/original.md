```
profile(h::Hist2D, axis::Symbol=:x)
profile(axis::Symbol=:x) = h::Hist2D -> profile(h, axis)
```

Returns the `axis`-profile of the 2D histogram by calculating the weighted mean over the other axis. `profile(h, :x)` will return a `Hist1D` with the y-axis edges of `h`.
