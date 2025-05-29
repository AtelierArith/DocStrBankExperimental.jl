```
GeodesicLength(DM::DataModel,sol::AbstractODESolution, Endrange::Number=sol.t[end]; FullSol::Bool=false, tol=1e-14)
GeodesicLength(Metric::Function,sol::AbstractODESolution, Endrange::Number=sol.t[end]; FullSol::Bool=false, tol=1e-14)
```

Calculates the length of a geodesic `sol` using the `Metric` up to parameter value `Endrange`.

$$
L[\gamma] \coloneqq \int_a^b \mathrm{d} t \, \sqrt{g_{\gamma(t)} \big(\dot{\gamma}(t), \dot{\gamma}(t)\big)}
$$
