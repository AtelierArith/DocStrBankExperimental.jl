```
DelayEmbedding(γ, τ, h = nothing) → `embedding`
```

Return a delay coordinates embedding structure to be used as a function-like-object, given a timeseries and some index. Calling

```julia
embedding(s, n)
```

will create the `n`-th delay vector of the embedded space, which has `γ` temporal neighbors with delay(s) `τ`. `γ` is the embedding dimension minus 1, `τ` is the delay time(s) while `h` are extra weights, as in [`embed`](@ref) for more.

**Be very careful when choosing `n`, because `@inbounds` is used internally.** Use [`τrange`](@ref)!
