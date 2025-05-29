```
LogarithmicMap(Metric::Function, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-9)
```

Computes the inverse of the differential-geometric exponential map, i.e. $\mathrm{ln}_p(q) \equiv (\mathrm{exp}^{-1})_p(q)$ which returns a (possibly non-unique!) initial direction $v \in T_p \mathcal{M}$ for a geodesic $\gamma:[0,1] \longrightarrow \mathcal{M}$ that goes from $p \in \mathcal{M}$ to $q \in \mathcal{M}$.
