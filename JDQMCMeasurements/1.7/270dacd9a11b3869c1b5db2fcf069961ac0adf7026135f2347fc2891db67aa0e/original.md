```
bond_correlation!(
    BB::AbstractArray{C,D},
    b′::Bond{D}, b″::Bond{D}, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gσ′_τ0::AbstractMatrix{T}, Gσ′_0τ::AbstractMatrix{T},
    Gσ′_ττ::AbstractMatrix{T}, Gσ″_00::AbstractMatrix{T},
    σ′::Int, σ″::Int, sgn=one(C)
) where {D, C<:Number, T<:Number}
```

Calculate the spin-resolved uneqaul-time bond-bond correlation function

$$
\begin{align*}
    \mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)
        = \frac{1}{N}\sum_{\mathbf{i}} & \mathcal{B}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau,0)\\
        =\frac{1}{N}\sum_{\mathbf{i}} & \langle\hat{B}_{\sigma',\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)\hat{B}_{\sigma'',\mathbf{i},(\mathbf{r}'',c,d)}(0)\rangle,
\end{align*}
$$

where

$$
\begin{align*}
    \hat{B}_{\sigma,\mathbf{i},(\mathbf{r},a,b)}
        & = \hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}\hat{b}_{\sigma,\mathbf{i}}^{\phantom{\dagger}}+\hat{b}_{\sigma,\mathbf{i}}^{\dagger}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}\\
        & = -\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}\hat{b}_{\sigma,\mathbf{i}}^{\dagger}-\hat{b}_{\sigma,\mathbf{i}}^{\phantom{\dagger}}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}
\end{align*}
$$

is the bond operator.

# Fields

  * `BB::AbstractArray{C,D}`: Array the spin-resolved bond correlation function $\mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)$ is added to.
  * `b′::Bond{D}`: Bond defining the bond operator appearing on the left side of the bond correlation function.
  * `b″::Bond{D}`: Bond defining the bond operator appearing on the right side of the bond correlation function.
  * `unit_cell::UnitCell{D}`: Defines unit cell.
  * `lattice::Lattice{D}`: Specifies size of finite lattice.
  * `Gσ′_τ0::AbstractMatrix{T}`: The matrix $G_{\sigma'}(\tau,0).$
  * `Gσ′_0τ::AbstractMatrix{T}`: The matrix $G_{\sigma'}(0,\tau).$
  * `Gσ′_ττ::AbstractMatrix{T}`: The matrix $G_{\sigma'}(\tau,\tau).$
  * `Gσ″_00::AbstractMatrix{T}`: The matrix $G_{\sigma''}(0,0).$
  * `σ′::Int`: The electron spin appearing in the $\hat{B}_{\sigma',\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}$ bond operator.
  * `σ″::Int`: The electron spin appearing in the $\hat{B}_{\sigma'',\mathbf{i},(\mathbf{r}'',c,d)}$ bond operator.
  * `sgn=one(C)`: The sign of the weight appearing in a DQMC simulation.
