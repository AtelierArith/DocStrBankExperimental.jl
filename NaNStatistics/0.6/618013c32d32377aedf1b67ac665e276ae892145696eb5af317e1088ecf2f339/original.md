```julia
nanquantile(A, q; dims)
```

Compute the `q`th quantile (where `q ∈ [0,1]`) of all elements in `A`, ignoring `NaN`s, optionally over dimensions specified by `dims`.

Reduction over multiple `dims` is not officially supported, though does work (in generally suboptimal time) as long as the dimensions being reduced over are all contiguous.

See also `nanquantile!` for a more efficient in-place variant.
