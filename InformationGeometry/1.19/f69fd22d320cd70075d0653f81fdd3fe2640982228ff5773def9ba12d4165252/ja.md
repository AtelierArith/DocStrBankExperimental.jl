```
ExponentialMap(Metric::Function, point::AbstractVector{<:Number}, tangent::AbstractVector{<:Number}; tol::Real=1e-9)
```

微分幾何的指数写像 $\mathrm{exp}_p(v)$ を計算し、初期方向 $v \in T_p \mathcal{M}$ を持つ測地線 $\gamma:[0,1] \longrightarrow \mathcal{M}$ によって到達される終点を返します。
