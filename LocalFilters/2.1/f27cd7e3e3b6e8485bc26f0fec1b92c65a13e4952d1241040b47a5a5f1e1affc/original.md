```
top_hat(A, B=3[, C]; order=FORWARD_FILTER, slow=false) -> dst
```

performs a *summit detection* by applying a top-hat filter to array `A` using the structuring element defined by `B` for the feature detection. Top-hat filtering is equivalent to:

```
dst = A .- opening(A, B)
```

Optional argument `C` specifies the structuring element for smoothing `A` prior to top-hat filtering. If `B` and `C` are specified as the radii of the structuring elements, then `C` should be smaller than `B`. For instance:

```
top_hat(bitmap, 3, 1)
```

may be used to detect text or lines in a bitmap image.

Keyword `order` specifies the filter(s) direction(s), `FORWARD_FILTER` by default. If `C` is specified, `order` may be a 2-tuple to specify a first order for `B` and a second one for `C`.

See [`bottom_hat`](@ref) for a related operation, [`LocalFilters.top_hat!`](@ref) for an in-place version.
