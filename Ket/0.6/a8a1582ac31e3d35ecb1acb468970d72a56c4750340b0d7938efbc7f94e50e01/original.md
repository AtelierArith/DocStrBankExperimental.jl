```
tensor_collinsgisin(p::Array, behaviour::Bool = false; correlation::Bool = false)
```

Converts a multipartite Bell functional `p` into Collins-Gisin notation. If `correlation` is `true`, `p` is assumed to be written in correlation notation. Otherwise, `p` is assumed to be written in probability notation. If `behaviour` is `true` do instead the transformation for behaviours. Doesn't assume normalization.

Also accepts the arguments of `tensor_probability` (state and measurements) for convenience.
