```
replaceprime[!](A::ITensor, plold::Int, plnew::Int; <keyword arguments>) -> ITensor
replaceprime[!](A::ITensor, plold => plnew; <keyword arguments>) -> ITensor
mapprime[!](A::ITensor, <arguments>; <keyword arguments>) -> ITensor

replaceprime(inds, plold::Int, plnew::Int; <keyword arguments>)
replaceprime(inds::IndexSet, plold => plnew; <keyword arguments>)
mapprime(inds, <arguments>; <keyword arguments>)
```

Set the prime level of the indices of an ITensor or collection of indices with prime level `plold` to `plnew`.

Optionally, only modify the indices with the specified keyword arguments.

# Arguments

  * `tags = nothing`: if specified, only modify Index `i` if `hastags(i, tags) == true`.
  * `plev = nothing`: if specified, only modify Index `i` if `hasplev(i, plev) == true`.

The ITensor functions come in two versions, `f` and `f!`. The latter modifies the ITensor in-place. In both versions, the ITensor storage is not modified or copied (so it returns an ITensor with a view of the original storage).
