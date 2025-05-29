```
bernoulli_cache(n::Int)
```

Precomputes and caches all the Bernoulli numbers up to $B_n$. This is much faster than repeatedly calling `bernoulli(k)`. Once cached, subsequent calls to `bernoulli(k)` for any $k \le n$ will read from the cache, making them virtually free.

See also [`bernoulli`](@ref).

# Examples

```jldoctest
julia> bernoulli_cache(100)

julia> e = bernoulli(100)
-94598037819122125295227433069493721872702841533066936133385696204311395415197247711//33330
```
