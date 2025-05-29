```
WindowViewer(x; width, stride)
```

Initialize an iterator that generates views over the given timeseries `x` based on a window with a given `width`, incrementing the window views with the given `stride`. You can use this directly with `map`, such as `map(std, WindowViewer(x, ...))` would give you the moving-window-timeseries of the `std` of `x`.

If not given, the keywords `width, stride` are respectively taken as `default_window_width(x)` and `1`.
