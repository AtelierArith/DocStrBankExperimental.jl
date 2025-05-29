```
MTDelayEmbedding(γ, τ, B) -> `embedding`
```

Return a delay coordinates embedding structure to be used as a functor, that embeds multiple timeseries (`B` in total) given in the form of a [`Dataset`](@ref).

Calling

```julia
embedding(s, n)
```

where `s` is a `Dataset` will create the `n`-th delay vector of the embedded space, which has `γ` temporal neighbors with delay(s) `τ`. See [`reconstruct`](@ref) for more.

**Be very careful when choosing `n`, because `@inbounds` is used internally.** Use [`τrange`](@ref)!
