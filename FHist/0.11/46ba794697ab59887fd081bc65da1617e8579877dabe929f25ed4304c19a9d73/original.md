```
restrict(h::Hist2D, xlow=-Inf, xhigh=Inf, ylow=-Inf, yhigh=Inf)
restrict(xlow=-Inf, xhigh=Inf, ylow=-Inf, yhigh=Inf) = h::Hist2D -> restrict(h, xlow, xhigh, ylow, yhigh)
```

Returns a new histogram with a restricted x-axis. `restrict(h, 0, 3)` (or `h |> restrict(0, 3)`) will return a slice of `h` where the bin centers are in `[0, 3]` (inclusive).
