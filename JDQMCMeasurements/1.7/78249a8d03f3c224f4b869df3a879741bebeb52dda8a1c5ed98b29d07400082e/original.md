```
density_correlation!(
    DD::AbstractArray{C,D},
    a::Int, b::Int, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gσ_τ0::AbstractMatrix{T}, Gσ_0τ::AbstractMatrix{T},
    Gσ_ττ::AbstractMatrix{T}, Gσ′_00::AbstractMatrix{T},
    σ::Int, σ′::Int, sgn=one(C)
) where {D, C<:Number, T<:Number}
```

Calculate the spin-resolved unequal-time density correlation function

$$
\begin{align*}
    \mathcal{D}_{\mathbf{r}}^{(a,\sigma),(b,\sigma')}(\tau)
            = \frac{1}{N}\sum_{\mathbf{i}} & \mathcal{D}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{(a,\sigma),(b,\sigma')}(\tau,0) \\
            = \frac{1}{N}\sum_{\mathbf{i}} & \langle\hat{n}_{\sigma,a,\mathbf{i}+\mathbf{r}}(\tau)\hat{n}_{\sigma',b,\mathbf{r}}(0)\rangle,
\end{align*}
$$

where $\hat{n}_{\sigma', b,\mathbf{i}} = \hat{b}^\dagger_{\sigma', \mathbf{i}} \hat{b}_{\sigma, \mathbf{i}}$ is the number operator for an electron with spin $\sigma'$ on orbital $b$ in unit cell $\mathbf{i}$, with the result being added to the array `DD`.

# Fields

  * `DD::AbstractArray{C,D}`: The array the spin-resolved density correlation $\mathcal{D}_{\mathbf{r}}^{(a,\sigma),(b,\sigma')}(\tau)$ is added to.
  * `a::Int`: Index specifying an orbital species in the unit cell.
  * `b::Int`: Index specifying an orbital species in the unit cell.
  * `unit_cell::UnitCell{D}`: Defines unit cell.
  * `lattice::Lattice{D}`: Specifies size of finite lattice.
  * `Gσ_τ0::AbstractMatrix{T}`: The matrix $G_{\sigma}(\tau,0).$
  * `Gσ_0τ::AbstractMatrix{T}`: The matrix $G_{\sigma}(0,\tau).$
  * `Gσ_ττ::AbstractMatrix{T}`: The matrix $G_{\sigma}(\tau,\tau).$
  * `Gσ′_00::AbstractMatrix{T}`: The matrix $G_{\sigma'}(0,0).$
  * `σ::Int`: The electron spin appearing in the $\langle \hat{n} \rangle_{\sigma,a,\mathbf{i}+\mathbf{r}}$ density operator.
  * `σ′::Int`: The electron spin appearing in the $\langle \hat{n} \rangle_{\sigma',b,\mathbf{i}}$ density operator.
  * `sgn=one(C)`: The sign of the weight appearing in a DQMC simulation.
