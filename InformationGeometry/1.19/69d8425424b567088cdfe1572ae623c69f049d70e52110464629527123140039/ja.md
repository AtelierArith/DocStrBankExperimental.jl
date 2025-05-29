```
GeodesicLength(DM::DataModel,sol::AbstractODESolution, Endrange::Number=sol.t[end]; FullSol::Bool=false, tol=1e-14)
GeodesicLength(Metric::Function,sol::AbstractODESolution, Endrange::Number=sol.t[end]; FullSol::Bool=false, tol=1e-14)
```

ジオデシック `sol` の長さを、パラメータ値 `Endrange` まで `Metric` を使用して計算します。

$$
L[\gamma] \coloneqq \int_a^b \mathrm{d} t \, \sqrt{g_{\gamma(t)} \big(\dot{\gamma}(t), \dot{\gamma}(t)\big)}
$$
