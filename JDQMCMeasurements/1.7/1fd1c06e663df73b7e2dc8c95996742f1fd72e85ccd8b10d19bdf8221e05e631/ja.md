```
spin_z_correlation!(
    SzSz::AbstractArray{C,D},
    a::Int, b::Int, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gup_τ0::AbstractMatrix{T}, Gup_0τ::AbstractMatrix{T},
    Gup_ττ::AbstractMatrix{T}, Gup_00::AbstractMatrix{T},
    Gdn_τ0::AbstractMatrix{T}, Gdn_0τ::AbstractMatrix{T},
    Gdn_ττ::AbstractMatrix{T}, Gdn_00::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Complex, T<:Number}
```

$$
\hat{z}
$$

方向の不等時スピン-スピン相関関数は次のように与えられます。

$$
\begin{align*}
\mathcal{S}_{z,\mathbf{r}}^{a,b}(\tau)=\frac{1}{N}\sum_{\mathbf{i}}\mathcal{S}_{z,\mathbf{i}+\mathbf{r},\mathbf{i}}^{ab}(\tau,0) 
    = & \frac{1}{N}\sum_{\mathbf{i}}\big\langle\hat{S}_{z,a,\mathbf{i}+\mathbf{r}}(\tau)\hat{S}_{z,b,\mathbf{i}}(0)\big\rangle,
\end{align*}
$$

ここで、スピン-$\hat{z}$演算子は次のように与えられます。

$$
\begin{align*}
\hat{S}_{z,a,\mathbf{i}}= & (\hat{a}_{\uparrow,\mathbf{i}}^{\dagger},\hat{a}_{\downarrow,\mathbf{i}}^{\dagger})\left[\begin{array}{cc}
1 & 0\\
0 & -1
\end{array}\right]\left(\begin{array}{c}
\hat{a}_{\uparrow,\mathbf{i}}\\
\hat{a}_{\downarrow,\mathbf{i}}
\end{array}\right)\\
= & \hat{n}_{\uparrow,a,\mathbf{i}}-\hat{n}_{\downarrow,a,\mathbf{i}}.
\end{align*}
$$

# フィールド

  * `SzSz::AbstractArray{C,D}`: スピン-$z$相関関数 $\mathcal{S}_{z,\mathbf{r}}^{a,b}(\tau)$ が追加される配列。
  * `a::Int`: 単位格子内の軌道種を指定するインデックス。
  * `b::Int`: 単位格子内の軌道種を指定するインデックス。
  * `unit_cell::UnitCell{D}`: 単位格子を定義します。
  * `lattice::Lattice{D}`: 有限格子のサイズを指定します。
  * `Gup_τ0::AbstractMatrix{T}`: 行列 $G_{\uparrow}(\tau,0).$
  * `Gup_0τ::AbstractMatrix{T}`: 行列 $G_{\uparrow}(0,\tau).$
  * `Gup_ττ::AbstractMatrix{T}`: 行列 $G_{\uparrow}(\tau,\tau).$
  * `Gup_00::AbstractMatrix{T}`: 行列 $G_{\uparrow}(0,0).$
  * `Gdn_τ0::AbstractMatrix{T}`: 行列 $G_{\downarrow}(\tau,0).$
  * `Gdn_0τ::AbstractMatrix{T}`: 行列 $G_{\downarrow}(0,\tau).$
  * `Gdn_ττ::AbstractMatrix{T}`: 行列 $G_{\downarrow}(\tau,\tau).$
  * `Gdn_00::AbstractMatrix{T}`: 行列 $G_{\downarrow}(0,0).$
  * `sgn=one(C)`: DQMCシミュレーションに現れる重みの符号。
