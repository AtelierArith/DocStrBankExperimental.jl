```
SR1 <: AbstractQuasiNewtonUpdateRule
```

indicates in [`AbstractQuasiNewtonDirectionUpdate`](@ref) that the Riemannian SR1 update is used in the Riemannian quasi-Newton method.

Denote by $\widetilde{H}_k^\mathrm{SR1}$ the operator concatenated with a vector transport and its inverse before and after to act on $x_{k+1} = R_{x_k}(α_k η_k)$. Then the update formula reads

$$
H^\mathrm{SR1}_{k+1} = \widetilde{H}^\mathrm{SR1}_k
+ \frac{
  (y_k - \widetilde{H}^\mathrm{SR1}_k s_k) (y_k - \widetilde{H}^\mathrm{SR1}_k s_k)^{\mathrm{T}}
}{
(y_k - \widetilde{H}^\mathrm{SR1}_k s_k)^{\mathrm{T}} s_k
}
$$

where $s_k$ and $y_k$ are the coordinate vectors with respect to the current basis (from [`QuasiNewtonState`](@ref)) of

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{and}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

respectively.

This method can be stabilized by only performing the update if denominator is larger than $r\lVert s_k\rVert_{x_{k+1}}\lVert y_k - \widetilde{H}^\mathrm{SR1}_k s_k \rVert_{x_{k+1}}$ for some $r>0$. For more details, see Section 6.2 in [NocedalWright:2006](@cite).

# Constructor

```
SR1(r::Float64=-1.0)
```

Generate the `SR1` update.
