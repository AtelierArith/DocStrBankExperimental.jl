```
genembed(s, τs, js = ones(...); ws = nothing) → ssset
```

Create a generalized embedding of `s` which can be a timeseries or arbitrary `StateSpaceSet`, and return the result as a new `StateSpaceSet`.

The generalized embedding works as follows:

  * `τs` denotes what delay times will be used for each of the entries of the delay vector. It is recommended that `τs[1] = 0`. `τs` is allowed to have *negative entries* as well.
  * `js` denotes which of the timeseries contained in `s` will be used for the entries of the delay vector. `js` can contain duplicate indices.
  * `ws` are optional weights that weight each embedded entry (the i-th entry of the   delay vector is weighted by `ws[i]`). If provided, it is recommended that `ws[1] == 1`.

`τs, js, ws` are tuples (or vectors) of length `D`, which also coincides with the embedding dimension. For example, imagine input trajectory $s = [x, y, z]$ where $x, y, z$ are timeseries (the columns of the `StateSpaceSet`). If `js = (1, 3, 2)` and `τs = (0, 2, -7)` the created delay vector at each step $n$ will be

$$
(x(n), z(n+2), y(n-7))
$$

Using `ws = (1, 0.5, 0.25)` as well would create

$$
(x(n), \frac{1}{2} z(n+2), \frac{1}{4} y(n-7))
$$

`js` can be skipped, defaulting to index 1 (first timeseries) for all delay entries, while it has no effect if `s` is a timeseries instead of a `StateSpaceSet`.

See also [`embed`](@ref). Internally uses [`GeneralizedEmbedding`](@ref).
