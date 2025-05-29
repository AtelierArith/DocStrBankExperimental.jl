```
distance(M::AbstractManifold, p, q)
```

Shortest distance between the points `p` and `q` on the [`AbstractManifold`](@ref) `M`, i.e.

$$
d(p,q) = \inf_{γ} L(γ),
$$

where the infimum is over all piecewise smooth curves $γ: [a,b] \to \mathcal M$ connecting $γ(a)=p$ and $γ(b)=q$ and

$$
L(γ) = \displaystyle\int_{a}^{b} \lVert \dotγ(t)\rVert_{γ(t)} \mathrm{d}t
$$

is the length of the curve $γ$.

If $\mathcal M$ is not connected, i.e. consists of several disjoint components, the distance between two points from different components should be $∞$.
