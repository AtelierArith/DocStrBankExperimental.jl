```
controller_reduction_plot(G, K)
```

Plot the normalized-coprime margin ([`ncfmargin`](@ref)) as a function of controller order when [`baltrunc_coprime`](@ref) is used to reduce the controller. Red, orange and green bands correspond to rules of thumb for bad, okay and good coprime uncertainty margins. A value of 0 indicate an unstable closed loop.

If `G` is an ExtendedStateSpace system, a second plot will be shown indicating the $H_∞$ norm between inputs and performance outputs $||T_{zw}||_\infty$ when the function [`controller_reduction`](@ref) is used to reduce the controller.

The order of the controller can safely be reduced as long as the normalized coprime margin remains sufficiently large. If the controller contains integrators, it may be advicable to protect the integrators from the reduction, e.g., if the controller is obtained using [`glover_mcfarlane`](@ref), perform the reduction on `info.Gs, info.Ks` rather than on `K`, and form `Kr` using the reduced `Ks`.

See [`glover_mcfarlane`](@ref) or [the docs](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/#Example-of-controller-reduction:) for an example.
