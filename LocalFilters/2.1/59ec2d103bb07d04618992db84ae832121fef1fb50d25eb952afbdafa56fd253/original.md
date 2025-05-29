```
LocalFilters.bottom_hat!(dst, wrk, A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

overwrites `dst` with the result of a bottom-hat filter applied to `A` with structuring element `B` and optional smoothing element `C`. Argument `wrk` is a workspace array whose contents is not preserved. The arguments `A`, `dst`, and `wrk` must be similar but different arrays. The destination `dst` is returned.

See also [`bottom_hat`](@ref) for more details.
