```
restrict(h::Hist1D, low=-Inf, high=Inf)
restrict(low=-Inf, high=Inf) = h::Hist1D -> restrict(h, low, high)
```

Returns a new histogram with a restricted x-axis. `restrict(h, 0, 3)` (or `h |> restrict(0, 3)`) will return a slice of `h` where the bin centers are in `[0, 3]` (inclusive).
