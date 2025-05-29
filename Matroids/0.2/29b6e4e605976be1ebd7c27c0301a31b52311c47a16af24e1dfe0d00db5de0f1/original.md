```
rank(M::Matroid, X::Set{T})::Int where {T<:Integer}
rank(M::Matroid)::Int
```

Return the rank of the set `X` in the matroid `M`.

We support alternative ways to invoke `rank`: For example, `rank(M,a,b,c)` and `rank(M,[a,b,c])` are the same as `rank(M,Set([a,b,c]))`.

Without `X`, return the rank of the matroid `M`.
