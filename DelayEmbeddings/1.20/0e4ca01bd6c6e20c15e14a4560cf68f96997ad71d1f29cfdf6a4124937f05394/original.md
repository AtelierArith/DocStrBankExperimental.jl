```
uzal_cost_local(Y::Dataset; kwargs...) → L_local
```

Compute the local L-statistic `L_local` for input dataset `Y` according to Uzal et al.[^Uzal2011]. The length of `L_local` is `length(Y)-Tw` and denotes a value of the local cost-function to each of the points of the state space trajectory.

In contrast to [`uzal_cost`](@ref) `σ²` here does not get averaged over all the state space reference points on the attractor. Therefore, the mean of 'L*local' is different to `L`, when calling `uzal*cost`, since the averaging is performed before logarithmizing.

Keywords as in [`uzal_cost`](@ref).

[^Uzal2011]: Uzal, L. C., Grinblat, G. L., Verdes, P. F. (2011). [Optimal reconstruction of dynamical systems: A noise amplification approach. Physical Review E 84, 016223](https://doi.org/10.1103/PhysRevE.84.016223).
