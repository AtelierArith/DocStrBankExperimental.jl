```
InverseBroyden <: AbstractQuasiNewtonUpdateRule
```

Indicates in [`AbstractQuasiNewtonDirectionUpdate`](@ref) that the Riemannian Broyden update is used in the Riemannian quasi-Newton method, which is as a convex combination of [`InverseBFGS`](@ref) and [`InverseDFP`](@ref).

Denote by $\widetilde{H}_k^\mathrm{Br}$ the operator concatenated with a vector transport and its inverse before and after to act on $x_{k+1} = R_{x_k}(α_k η_k)$. Then the update formula reads

$$
B^\mathrm{Br}_{k+1} = \widetilde{B}^\mathrm{Br}_k
 - \frac{\widetilde{B}^\mathrm{Br}_k y_k y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k}{y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k}
   + \frac{s_k s^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
 + φ_k y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k
 \Bigl(
     \frac{s_k}{s^{\mathrm{T}}_k y_k} - \frac{\widetilde{B}^\mathrm{Br}_k y_k}{y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k}
    \Bigr) \Bigl(
        \frac{s_k}{s^{\mathrm{T}}_k y_k} - \frac{\widetilde{B}^\mathrm{Br}_k y_k}{y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k}
 \Bigr)^{\mathrm{T}}
$$

where $s_k$ and $y_k$ are the coordinate vectors with respect to the current basis (from [`QuasiNewtonState`](@ref)) of

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{and}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

respectively, and $φ_k$ is the Broyden factor which is `:constant` by default but can also be set to `:Davidon`.

# Constructor

```
InverseBroyden(φ, update_rule::Symbol = :constant)
```
