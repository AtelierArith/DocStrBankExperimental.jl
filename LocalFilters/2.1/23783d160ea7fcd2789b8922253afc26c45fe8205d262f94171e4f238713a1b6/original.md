```
LocalFilters.top_hat!(dst, wrk, A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

overwrites `dst` with the result of a top-hat filter applied to `A` with structuring element `B`, and using `wrk` as a workspace whose contents is not preserved. The arguments `A`, `dst`, and `wrk` must be similar but different arrays. The destination `dst` is returned.

See also [`top_hat`](@ref) for more details.
