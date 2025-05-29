```
mapobs(f, data; batched=:auto)
```

Lazily map `f` over the observations in a data container `data`. Returns a new data container `mdata` that can be indexed and has a length. Indexing triggers the transformation `f`.

The batched keyword argument controls the behavior of `mdata[idx]` and `mdata[idxs]`  where `idx` is an integer and `idxs` is a vector of integers:

  * `batched=:auto` (default). Let `f` handle the two cases.   Calls `f(getobs(data, idx))` and `f(getobs(data, idxs))`.
  * `batched=:never`. The function `f` is always called on a single observation.   Calls `f(getobs(data, idx))` and `[f(getobs(data, idx)) for idx in idxs]`.
  * `batched=:always`. The function `f` is always called on a batch of observations.   Calls `getobs(f(getobs(data, [idx])), 1)` and `f(getobs(data, idxs))`.

# Examples

```julia
julia> data = (a=[1,2,3], b=[1,2,3]);

julia> mdata = mapobs(data) do x
         (c = x.a .+ x.b,  d = x.a .- x.b)
       end
mapobs(#25, (a = [1, 2, 3], b = [1, 2, 3]); batched=:auto))

julia> mdata[1]
(c = 2, d = 0)

julia> mdata[1:2]
(c = [2, 4], d = [0, 0])
```
