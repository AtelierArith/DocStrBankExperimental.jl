```
controller_reduction(P::ExtendedStateSpace, K, r, out=true; kwargs...)
```

Minimize    ||(K-Kᵣ) W||∞ if out=false             ||W (K-Kᵣ)||∞ if out=true See Robust and Optimal Control Ch 19.1 out indicates if the weight will be applied as output or input weight.

This function expects a *positive feedback controller `K`.

This method corresponds to the methods labelled SW1/SW2(SPA) in  Andreas Varga, "Controller Reduction Using Accuracy-Enhancing Methods" SW1 is the default method, corresponding to `out=true`.

This method does not support unstable controllers. See the reference above for alternatives. See also [`stab_unstab`](@ref) and [`baltrunc_unstab`](@ref).
