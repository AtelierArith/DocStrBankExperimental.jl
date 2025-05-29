Constructs a Smolyak approximation plan, given the `node_type` function, the number of dimensions, `d`, the approximation layers, `mu`, and the approximation `domain` (defaults to [1.0,-1.0]^d).  Returns an SApproxPlan struct.

# Signature

splan = smolyal*plan(node*type,d,mu,domain)

# Examples

```
julia> splan = smolyak_plan(chebyshev_extrema,2,2)
julia> splan = smolyak_plan(clenshaw_curtis_equidistant,2,[2,2])
julia> splan = smolyak_plan(chebyshev_extrema,2,2,[3.0 1.5; 2.0 0.5])
julia> splan = smolyak_plan(clenshaw_curtis_equidistant,2,[2,2],[3.0 1.5; 2.0 0.5])
```
