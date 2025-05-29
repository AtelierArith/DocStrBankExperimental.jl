`FixedSizeDiffCache(u::AbstractArray, N = Val{default_cache_size(length(u))})`

Builds a `FixedSizeDiffCache` object that stores both a version of the cache for `u` and for the `Dual` version of `u`, allowing use of pre-cached vectors with forward-mode automatic differentiation.
