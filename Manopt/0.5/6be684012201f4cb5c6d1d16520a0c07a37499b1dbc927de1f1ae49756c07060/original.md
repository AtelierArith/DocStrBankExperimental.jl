```
DFP <: AbstractQuasiNewtonUpdateRule
```

indicates in an [`AbstractQuasiNewtonDirectionUpdate`](@ref) that the Riemannian DFP update is used in the Riemannian quasi-Newton method.

Denote by $\widetilde{H}_k^\mathrm{DFP}$ the operator concatenated with a vector transport and its inverse before and after to act on $x_{k+1} = R_{x_k}(α_k η_k)$. Then the update formula reads

$$
H^\mathrm{DFP}_{k+1} = \Bigl(
  \mathrm{id}_{T_{x_{k+1}} \mathcal{M}} - \frac{y_k s^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
\Bigr)
\widetilde{H}^\mathrm{DFP}_k
\Bigl(
  \mathrm{id}_{T_{x_{k+1}} \mathcal{M}} - \frac{s_k y^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
\Bigr) + \frac{y_k y^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
$$

where $s_k$ and $y_k$ are the coordinate vectors with respect to the current basis (from [`QuasiNewtonState`](@ref)) of

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{and}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

respectively.
