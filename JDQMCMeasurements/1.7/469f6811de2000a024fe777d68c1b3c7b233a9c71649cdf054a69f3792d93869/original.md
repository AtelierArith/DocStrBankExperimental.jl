```
bond_correlation!(
    BB::AbstractArray{C,D},
    b′::Bond{D}, b″::Bond{D}, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gup_τ0::AbstractMatrix{T}, Gup_0τ::AbstractMatrix{T},
    Gup_ττ::AbstractMatrix{T}, Gup_00::AbstractMatrix{T},
    Gdn_τ0::AbstractMatrix{T}, Gdn_0τ::AbstractMatrix{T},
    Gdn_ττ::AbstractMatrix{T}, Gdn_00::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Number, T<:Number}
```

Calculate the uneqaul-time bond-bond correlation function

$$
\begin{align*}
\mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau) =
    & \frac{1}{N}\sum_{\mathbf{i}} \langle[\hat{B}_{\uparrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)+\hat{B}_{\downarrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)]
                                   \cdot[\hat{B}_{\uparrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)+\hat{B}_{\downarrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)]\rangle
\end{align*}
$$

where the

$$
\hat{B}_{\sigma,\mathbf{i},(\mathbf{r},a,b)}
    = \hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}\hat{b}_{\sigma,\mathbf{i}}^{\phantom{\dagger}}
    + \hat{b}_{\sigma,\mathbf{i}}^{\dagger}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}
$$

is the bond operator.

# Fields

  * `BB::AbstractArray{C,D}`: Array the bond correlation function $\mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau)$ is added to.
  * `b′::Bond{D}`: Bond defining the bond operator appearing on the left side of the bond correlation function.
  * `b″::Bond{D}`: Bond defining the bond operator appearing on the right side of the bond correlation function.
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
