```
ExponentialMap(Metric::Function, point::AbstractVector{<:Number}, tangent::AbstractVector{<:Number}; tol::Real=1e-9)
```

Computes the differential-geometric exponential map $\mathrm{exp}_p(v)$ which returns the endpoint that is reached by a geodesic $\gamma:[0,1] \longrightarrow \mathcal{M}$ with initial direction $v \in T_p \mathcal{M}$.
