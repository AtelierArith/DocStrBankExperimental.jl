```
bilateralfilter!(dst, A, F, G...; order = FORWARD_FILTER) -> dst
```

overwrites `dst` with the result of applying the bilateral filter on array `A` and returns `dst`.

See [`bilateralfilter`](@ref) for a description of the other arguments than `dst` and see [Wikipedia](https://en.wikipedia.org/wiki/Bilateral_filter) for a description of the bilateral filter.
