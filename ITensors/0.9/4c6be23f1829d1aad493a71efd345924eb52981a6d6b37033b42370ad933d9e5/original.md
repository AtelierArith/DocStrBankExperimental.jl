```
swapprime[!](A::ITensor, pl1::Int, pl2::Int; <keyword arguments>) -> ITensor
swapprime[!](A::ITensor, pl1 => pl2; <keyword arguments>) -> ITensor

swapprime(inds, pl1::Int, pl2::Int; <keyword arguments>)
swapprime(inds, pl1 => pl2; <keyword arguments>)
```

Set the prime level of the indices of an ITensor or collection of indices with prime level `pl1` to `pl2`, and those with prime level `pl2` to `pl1`.

Optionally, only modify the indices with the specified keyword arguments.

# Arguments

  * `tags = nothing`: if specified, only modify Index `i` if `hastags(i, tags) == true`.
  * `plev = nothing`: if specified, only modify Index `i` if `hasplev(i, plev) == true`.

The ITensor functions come in two versions, `f` and `f!`. The latter modifies the ITensor in-place. In both versions, the ITensor storage is not modified or copied (so it returns an ITensor with a view of the original storage).
