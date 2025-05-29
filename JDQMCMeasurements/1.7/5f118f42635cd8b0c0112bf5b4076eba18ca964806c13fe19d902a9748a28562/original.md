```
current_correlation!(
    CC::AbstractArray{C,D},
    b′::Bond{D}, b″::Bond{D},
    tup′::AbstractArray{T,D}, tup″::AbstractArray{T,D},
    tdn′::AbstractArray{T,D}, tdn″::AbstractArray{T,D},
    unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gup_τ0::AbstractMatrix{T}, Gup_0τ::AbstractMatrix{T},
    Gup_ττ::AbstractMatrix{T}, Gup_00::AbstractMatrix{T},
    Gdn_τ0::AbstractMatrix{T}, Gdn_0τ::AbstractMatrix{T},
    Gdn_ττ::AbstractMatrix{T}, Gdn_00::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Number, T<:Number}
```

Calculate the uneqaul-time current-current correlation function

$$
\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau) = \frac{1}{N}\sum_{\mathbf{i}}
    \langle[\hat{J}_{\uparrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)+\hat{J}_{\downarrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)]
    \cdot[\hat{J}_{\uparrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)+\hat{J}_{\downarrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)]\rangle,
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

  * `CC::AbstractArray{C,D}`: Array the current correlation function $\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau)$ is added to.
  * `b′::Bond{D}`: Bond defining the current operator appearing on the left side of the current correlation function.
  * `b″::Bond{D}`: Bond defining the current operator appearing on the right side of the current correlation function.
  * `tup′::AbstractArray{T,D}`: Spin up position and imaginary time dependent hopping amplitudes corresponding to bond `b′`.
  * `tup″::AbstractArray{T,D}`: Spin up position and imaginary time dependent hopping amplitudes corresponding to bond `b″`.
  * `tdn′::AbstractArray{T,D}`: Spin down position and imaginary time dependent hopping amplitudes corresponding to bond `b′`.
  * `tdn″::AbstractArray{T,D}`: Spin down position and imaginary time dependent hopping amplitudes corresponding to bond `b″`.
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
