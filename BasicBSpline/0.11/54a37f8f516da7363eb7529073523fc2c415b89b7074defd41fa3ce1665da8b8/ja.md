```
BSplineDerivativeSpace{r}(P::BSplineSpace)
```

与えられた微分次数とBスプライン空間からBスプライン空間の導関数を構築します。

$$
D^{r}(\mathcal{P}[p,k])
=\left\{t \mapsto \left. \frac{d^r f}{dt^r}(t) \  \right| \ f \in \mathcal{P}[p,k] \right\}
$$

# 例

```jldoctest
julia> P = BSplineSpace{2}(KnotVector([1,2,3,4,5,6]))
BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([1, 2, 3, 4, 5, 6]))

julia> dP = BSplineDerivativeSpace{1}(P)
BSplineDerivativeSpace{1, BSplineSpace{2, Int64, KnotVector{Int64}}, Int64}(BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([1, 2, 3, 4, 5, 6])))

julia> degree(P), degree(dP)
(2, 1)
```
