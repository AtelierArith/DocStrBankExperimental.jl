```
s(N::AbstractUnipartiteNetwork; dims::Union{Nothing,Integer}=nothing)
```

Computes the average weighted degree. This is proportional to the (weighted) density of interactions.

If dims is provided, the incoming (`dims=1`) or outgoing (`dims=2`) is computed.
