```
LogarithmicMap(Metric::Function, P::AbstractVector{<:Number}, Q::AbstractVector{<:Number}; tol::Real=1e-9)
```

微分幾何的指数写像の逆を計算します。すなわち、$\mathrm{ln}_p(q) \equiv (\mathrm{exp}^{-1})_p(q)$ であり、これは $p \in \mathcal{M}$ から $q \in \mathcal{M}$ へと進む測地線 $\gamma:[0,1] \longrightarrow \mathcal{M}$ の初期方向 $v \in T_p \mathcal{M}$ を（おそらく一意でない！）返します。
