```
bottom_hat(A, B=3[, C]; order=FORWARD_FILTER, slow=false) -> dst
```

performs a *valley detection* by applying a bottom-hat filter to array `A` using the structuring element defined by `B` for the feature detection. Bottom-hat filtering is equivalent to:

```
dst = closing(A, B) .- A
```

Optional argument `C` specifies the structuring element for smoothing `A` prior to bottom-hat filtering. If `B` and `C` are specified as the radii of the structuring elements, then `C` should be smaller than `B`.

Keyword `order` specifies the filter(s) direction(s), `FORWARD_FILTER` by default. If `C` is specified, `order` may be a 2-tuple to specify a first order for `B` and a second one for `C`.

See [`top_hat`](@ref) for a related operation, [`LocalFilters.bottom_hat!`](@ref) for an in-place version.
