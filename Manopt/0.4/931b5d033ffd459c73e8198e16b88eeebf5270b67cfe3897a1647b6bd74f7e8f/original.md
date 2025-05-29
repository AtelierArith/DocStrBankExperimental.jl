```
BFGS <: AbstractQuasiNewtonUpdateRule
```

indicates in [`AbstractQuasiNewtonDirectionUpdate`](@ref) that the Riemannian BFGS update is used in the Riemannian quasi-Newton method.

Denote by $\widetilde{H}_k^\mathrm{BFGS}$ the operator concatenated with a vector transport and its inverse before and after to act on $x_{k+1} = R_{x_k}(α_k η_k)$. Then the update formula reads

$$
H^\mathrm{BFGS}_{k+1} = \widetilde{H}^\mathrm{BFGS}_k  + \frac{y_k y^{\mathrm{T}}_k }{s^{\mathrm{T}}_k y_k} - \frac{\widetilde{H}^\mathrm{BFGS}_k s_k s^{\mathrm{T}}_k \widetilde{H}^\mathrm{BFGS}_k }{s^{\mathrm{T}}_k \widetilde{H}^\mathrm{BFGS}_k s_k}
$$

where $s_k$ and $y_k$ are the coordinate vectors with respect to the current basis (from [`QuasiNewtonState`](@ref)) of

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{and}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

respectively.
