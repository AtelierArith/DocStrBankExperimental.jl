```
greens!(
    G::AbstractArray{C,D},
    a::Int, b::Int, unit_cell::UnitCell{D}, lattice::Lattice{D},
    G_τ0::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Number, T<:Number}
```

Measure the unequal time Green's function averaged over translation symmetry

$$
G_{\sigma,\mathbf{r}}^{a,b}(\tau)=\frac{1}{N}\sum_{\mathbf{i}}G_{\sigma,\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b}(\tau,0)
=\frac{1}{N}\sum_{\mathbf{i}}\langle\hat{\mathcal{T}}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}(\tau)\hat{b}_{\sigma,\mathbf{i}}^{\dagger}(0)\rangle,
$$

with the result being added to `G`.

# Fields

  * `G::AbstractArray{C,D}`: Array the green's function $G_{\sigma,\mathbf{r}}^{a,b}(\tau)$ is written to.
  * `a::Int`: Index specifying an orbital species in the unit cell.
  * `b::Int`: Index specifying an orbital species in the unit cell.
  * `unit_cell::UnitCell{D}`: Defines unit cell.
  * `lattice::Lattice{D}`: Specifies size of finite lattice.
  * `G_τ0::AbstractMatrix{T}`: The matrix $G(\tau,0).$
  * `sgn=one(C)`: The sign of the weight appearing in a DQMC simulation.
