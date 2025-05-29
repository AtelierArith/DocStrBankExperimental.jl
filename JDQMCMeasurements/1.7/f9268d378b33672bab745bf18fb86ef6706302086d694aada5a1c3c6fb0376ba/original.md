```
current_correlation!(
    CC::AbstractArray{C,D},
    b′::Bond{D}, b″::Bond{D},
    t′::AbstractArray{T,D}, t″::AbstractArray{T,D},
    unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gσ′_τ0::AbstractMatrix{T}, Gσ′_0τ::AbstractMatrix{T},
    Gσ′_ττ::AbstractMatrix{T}, Gσ″_00::AbstractMatrix{T},
    σ′::Int, σ″::Int, sgn=one(C)
) where {D, C<:Number, T<:Number}
```

Calculate the spin-resolved uneqaul-time current-current correlation function

$$
\begin{align*}
\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)
    & = \frac{1}{N}\sum_{\mathbf{i}}\mathcal{J}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau,0)\\
    & = \frac{1}{N}\sum_{\mathbf{i}}\langle\hat{J}_{\sigma',\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)\hat{J}_{\sigma'',\mathbf{i},(\mathbf{r}'',c,d)}(0)\rangle,
\end{align*}
$$

where the spin-resolved current operator is given by

$$
\begin{align*}
    \hat{J}_{\sigma,\mathbf{i},(\mathbf{r},a,b)}
        & = -{\rm i}(t_{\sigma,\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b} \hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}\hat{b}_{\sigma,\mathbf{i}} - t_{\sigma,\mathbf{i}, \mathbf{i}+\mathbf{r}}^{b,a} \hat{b}_{\sigma,\mathbf{i}}^{\dagger}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}})\\
\end{align*}
$$

and $t_{\sigma,\mathbf{i}, \mathbf{i}+\mathbf{r}}^{b,a} = \big( t_{\sigma,\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b} \big)^*$.

# Fields

  * `CC::AbstractArray{C,D}`: Array the spin-resolved current correlation function $\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)$ is added to.
  * `b′::Bond{D}`: Bond defining the current operator appearing on the left side of the current correlation function.
  * `b″::Bond{D}`: Bond defining the current operator appearing on the right side of the current correlation function.
  * `t′::AbstractArray{T,D}`: Position and imaginary time dependent hopping amplitude associated with bond `b′`.
  * `t″::AbstractArray{T,D}`: Position and imaginary time dependent hopping amplitude associated with bond `b″`.
  * `unit_cell::UnitCell{D}`: Defines unit cell.
  * `lattice::Lattice{D}`: Specifies size of finite lattice.
  * `Gσ′_τ0::AbstractMatrix{T}`: The matrix $G_{\sigma'}(\tau,0).$
  * `Gσ′_0τ::AbstractMatrix{T}`: The matrix $G_{\sigma'}(0,\tau).$
  * `Gσ′_ττ::AbstractMatrix{T}`: The matrix $G_{\sigma'}(\tau,\tau).$
  * `Gσ″_00::AbstractMatrix{T}`: The matrix $G_{\sigma''}(0,0).$
  * `σ′::Int`: The electron spin appearing in the left current operator.
  * `σ″::Int`: The electron spin appearing in the right current operator.
  * `sgn=one(C)`: The sign of the weight appearing in a DQMC simulation.
