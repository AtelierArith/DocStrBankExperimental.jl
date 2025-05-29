```
density_correlation!(
    DD::AbstractArray{C,D},
    a::Int, b::Int, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gup_τ0::AbstractMatrix{T}, Gup_0τ::AbstractMatrix{T},
    Gup_ττ::AbstractMatrix{T}, Gup_00::AbstractMatrix{T},
    Gdn_τ0::AbstractMatrix{T}, Gdn_0τ::AbstractMatrix{T},
    Gdn_ττ::AbstractMatrix{T}, Gdn_00::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Number, T<:Number}
```

Calculate the unequal-time density-density (charge) correlation function

$$
\begin{align*}
\mathcal{D}_{\mathbf{r}}^{a,b}(\tau)
    & = \frac{1}{N}\sum_{\mathbf{i}} \mathcal{D}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b}(\tau,0)\\
    & = \frac{1}{N}\sum_{\mathbf{i}} \langle \hat{n}_{a,\mathbf{i} + \mathbf{r}}(\tau)\hat{n}_{b,\mathbf{i}}(0) \rangle,
\end{align*}
$$

where $\hat{n}_{b,\mathbf{i}} = (\hat{n}_{\uparrow, b, \mathbf{i}} + \hat{n}_{\downarrow, b, \mathbf{i}})$ and $\hat{n}_{\sigma, b,\mathbf{i}} = \hat{b}^\dagger_{\sigma, \mathbf{i}} \hat{b}_{\sigma, \mathbf{i}}$ is the number operator for an electron with spin $\sigma$ on orbital $b$ in unit cell $\mathbf{i}$, with the result being added to the array `DD`.

# Fields

  * `DD::AbstractArray{C,D}`: Array the density correlation function $\mathcal{D}_{\mathbf{r}}^{a,b}(\tau)$ is added to.
  * `a::Int`: Index specifying an orbital species in the unit cell.
  * `b::Int`: Index specifying an orbital species in the unit cell.
  * `unit_cell::UnitCell{D}`: Defines unit cell.
  * `lattice::Lattice{D}`: Specifies size of finite lattice.
  * `Gup_τ0::AbstractMatrix{T}`: The matrix $G_{\uparrow}(\tau,0).$
  * `Gup_0τ::AbstractMatrix{T}`: The matrix $G_{\uparrow}(0,\tau).$
  * `Gup_ττ::AbstractMatrix{T}`: The matrix $G_{\uparrow}(\tau,\tau).$
  * `Gup_00::AbstractMatrix{T}`: The matrix $G_{\uparrow}(0,0).$
  * `Gdn_τ0::AbstractMatrix{T}`: The matrix $G_{\downarrow}(\tau,0).$
  * `Gdn_0τ::AbstractMatrix{T}`: The matrix $G_{\downarrow}(0,\tau).$
  * `Gdn_ττ::AbstractMatrix{T}`: The matrix $G_{\downarrow}(\tau,\tau).$
  * `Gdn_00::AbstractMatrix{T}`: The matrix $G_{\downarrow}(0,0).$
  * `sgn=one(C)`: The sign of the weight appearing in a DQMC simulation.
