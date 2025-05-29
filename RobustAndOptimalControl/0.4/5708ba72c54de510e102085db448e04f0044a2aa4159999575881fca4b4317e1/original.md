```
K, γ, info = glover_mcfarlane(G::AbstractStateSpace{<:Discrete}, γ = 1.1; W1=1, W2=1, strictly_proper=false)
```

For discrete systems, the `info` tuple contains also feedback gains `F, L` and observer gain `Hkf` such that the controller on observer form is given by

$$
x^+ = Ax + Bu + H_{kf} (Cx - y)\\
u = Fx + L (Cx - y)
$$

Note, this controller is *not* strictly proper, i.e., it has a non-zero D matrix. The controller can be transformed to observer form for the scaled plant (`info.Gs`) by `Ko = observer_controller(info)`, in which case the following holds `G*K == info.Gs*Ko` (realizations are different).

If `strictly_proper = true`, the returned controller `K` will have `D == 0`. This can be advantageous in implementations where computational delays are present. In this case, `info.L == 0` as well.

Ref discrete version: Iglesias, "The Strictly Proper Discrete-Time Controller for the Normalized Left-Coprime Factorization Robust Stabilization Problem"
