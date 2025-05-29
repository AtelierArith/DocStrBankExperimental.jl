```julia
struct PkgCacheInfo
```

Objects stored the pkgimage. The main contents are the modules themselves, but some additional objects are stored external to the modules. It also contains the data used to perform invalidation-checks.

  * `cachefile`: The filename of the cache.

  * `modules`: The list of modules stored in the package image. The final one is the "top" package module.

  * `init_order`: The list of modules with an `__init__` function, in the order in which they should be called.

  * `external_methods`: The list of methods added to external modules. E.g., `Base.push!(v::MyNewVector, x)`.

  * `new_specializations`: The list of novel specializations of external methods that were created during package precompilation. E.g., `get(::Dict{String,Float16}, ::String, ::Nothing)`: `Base` owns the method and all the types in this specialization, but might not have precompiled it until it was needed by a package.

  * `new_method_roots`: New GC roots added to external methods. These are an important but internal detail of how type-inferred code is compressed for serialization.

  * `external_targets`: The list of already-inferred MethodInstances that get called by items stored in this cachefile. If any of these are no longer valid (or no longer the method that would be chosen by dispatch), then some compiled code in this package image must be invalidated and recompiled.

  * `edges`: A lookup table of `external_targets` dependencies: `[mi1, indxs1, mi2, indxs2...]` means that `mi1` (cached in this pkgimage) depends on `external_targets[idxs1]`; `mi2` depends on `external_targets[idxs2]`, and so on.

  * `filesize`: The total size of the cache file.

  * `cachesizes`: Sizes of the individual sections. See [`PkgCacheSizes`](@ref).

  * `image_targets`: The image targets that were cloned into the pkgimage, if used.
