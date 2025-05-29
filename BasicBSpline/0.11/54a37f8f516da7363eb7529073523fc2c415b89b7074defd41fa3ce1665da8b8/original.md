```
BSplineDerivativeSpace{r}(P::BSplineSpace)
```

Construct derivative of B-spline space from given differential order and B-spline space.

$$
D^{r}(\mathcal{P}[p,k])
=\left\{t \mapsto \left. \frac{d^r f}{dt^r}(t) \  \right| \ f \in \mathcal{P}[p,k] \right\}
$$

# Examples

```jldoctest
julia> P = BSplineSpace{2}(KnotVector([1,2,3,4,5,6]))
BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([1, 2, 3, 4, 5, 6]))

julia> dP = BSplineDerivativeSpace{1}(P)
BSplineDerivativeSpace{1, BSplineSpace{2, Int64, KnotVector{Int64}}, Int64}(BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([1, 2, 3, 4, 5, 6])))

julia> degree(P), degree(dP)
(2, 1)
```
