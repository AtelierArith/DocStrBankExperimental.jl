```
matching_cache_argtypes(𝕃::AbstractLattice, linfo::MethodInstance) ->
    (cache_argtypes::Vector{Any}, overridden_by_const::BitVector)
```

Returns argument types `cache_argtypes::Vector{Any}` for `linfo` that are in the native Julia type domain. `overridden_by_const::BitVector` is all `false` meaning that there is no additional extended lattice information there.

```
matching_cache_argtypes(𝕃::AbstractLattice, linfo::MethodInstance, argtypes::ForwardableArgtypes) ->
    (cache_argtypes::Vector{Any}, overridden_by_const::BitVector)
```

Returns cache-correct extended lattice argument types `cache_argtypes::Vector{Any}` for `linfo` given some `argtypes` accompanied by `overridden_by_const::BitVector` that marks which argument contains additional extended lattice information.

In theory, there could be a `cache` containing a matching `InferenceResult` for the provided `linfo` and `given_argtypes`. The purpose of this function is to return a valid value for `cache_lookup(𝕃, linfo, argtypes, cache).argtypes`, so that we can construct cache-correct `InferenceResult`s in the first place.
