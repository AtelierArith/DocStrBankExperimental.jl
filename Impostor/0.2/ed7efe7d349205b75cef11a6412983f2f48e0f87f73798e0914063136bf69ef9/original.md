```
surname(n::Integer = 1; kws...)
```

Generate a `surname` using the provided `locale` as source.

# Parameters

  * `n::Integer = 1`: number of surnames to generate.

# Kwargs

  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.
