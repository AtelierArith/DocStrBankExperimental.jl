```
swaptags[!](A::ITensor, ts1::String, ts2::String; <keyword arguments>) -> ITensor

swaptags(is::IndexSet, ts1::String, ts2::String; <keyword arguments>) -> IndexSet
```

Swap the tags `ts1` with `ts2` for the indices of an ITensor.

Optionally, only modify the indices with the specified keyword arguments.

# Arguments

  * `tags = nothing`: if specified, only modify Index `i` if `hastags(i, tags) == true`.
  * `plev = nothing`: if specified, only modify Index `i` if `hasplev(i, plev) == true`.

The ITensor functions come in two versions, `f` and `f!`. The latter modifies the ITensor in-place. In both versions, the ITensor storage is not modified or copied (so it returns an ITensor with a view of the original storage).
