```
GeneralizedEmbedding(τs, js = ones(length(τs)), ws = nothing) -> `embedding`
```

Return a delay coordinates embedding structure to be used as a function. Given a timeseries *or* trajectory (i.e. `StateSpaceSet`) `s` and calling

```julia
embedding(s, n)
```

will create the delay vector of the `n`-th point of `s` in the embedded space using generalized embedding (see [`genembed`](@ref)).

`js` is ignored for timeseries input `s` (since all entries of `js` must be `1` in this case) and in addition `js` defaults to `(1, ..., 1)` for all `τ`.

**Be very careful when choosing `n`, because `@inbounds` is used internally.** Use [`τrange`](@ref)!
