```
colorflow(flo; maxflow)
```

Visualize the given flow field `flo` by creating an image encoding direction as color and length as saturation (scaled using `maxflow`). Missing values are encoded as black. If `maxflow` is omitted, it will be computed from the input using the `maxflow` function.
