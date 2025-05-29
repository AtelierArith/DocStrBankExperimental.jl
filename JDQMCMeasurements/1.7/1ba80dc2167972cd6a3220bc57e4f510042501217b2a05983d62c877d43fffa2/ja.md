```
spin_x_correlation!(
    SxSx::AbstractArray{C,D}, a::Int, b::Int, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gup_τ0::AbstractMatrix{T}, Gup_0τ::AbstractMatrix{T},
    Gdn_τ0::AbstractMatrix{T}, Gdn_0τ::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Number, T<:Number}
```

$$
\hat{x}
$$

方向の不等時スピン-スピン相関関数は次のように与えられます。

$$
\mathcal{S}_{x,\mathbf{r}}^{a,b}(\tau)=\frac{1}{N}\sum_{\mathbf{i}}\mathcal{S}_{x,\mathbf{i}+\mathbf{r},\mathbf{i}}^{ab}(\tau,0)
=\frac{1}{N}\sum_{\mathbf{i}}\big\langle\hat{S}_{x,a,\mathbf{i}+\mathbf{r}}(\tau)\hat{S}_{x,b,\mathbf{i}}(0)\big\rangle,
$$

ここで、スピン-$\hat{x}$演算子は次のように与えられます。

$$
\begin{align*}
\hat{S}_{x,\mathbf{i},a}= & (\hat{a}_{\uparrow,\mathbf{i}}^{\dagger},\hat{a}_{\downarrow,\mathbf{i}}^{\dagger})\left[\begin{array}{cc}
0 & 1\\
1 & 0
\end{array}\right]\left(\begin{array}{c}
\hat{a}_{\uparrow,\mathbf{i}}\\
\hat{a}_{\downarrow,\mathbf{i}}
\end{array}\right)\\
= & \hat{a}_{\uparrow,\mathbf{i}}^{\dagger}\hat{a}_{\downarrow,\mathbf{i}}+\hat{a}_{\downarrow,\mathbf{i}}^{\dagger}\hat{a}_{\uparrow,\mathbf{i}}.
\end{align*}
$$

# フィールド

  * `SxSx::AbstractArray{C,D}`: スピン-$x$相関関数 $\mathcal{S}_{x,\mathbf{r}}^{a,b}(\tau)$ が追加される配列。
  * `a::Int`: 単位格子内の軌道種を指定するインデックス。
  * `b::Int`: 単位格子内の軌道種を指定するインデックス。
  * `unit_cell::UnitCell{D}`: 単位格子を定義します。
  * `lattice::Lattice{D}`: 有限格子のサイズを指定します。
  * `Gup_τ0::AbstractMatrix{T}`: 行列 $G_{\uparrow}(\tau,0).$
  * `Gup_0τ::AbstractMatrix{T}`: 行列 $G_{\uparrow}(0,\tau).$
  * `Gdn_τ0::AbstractMatrix{T}`: 行列 $G_{\downarrow}(\tau,0).$
  * `Gdn_0τ::AbstractMatrix{T}`: 行列 $G_{\downarrow}(0,\tau).$
  * `sgn=one(C)`: DQMCシミュレーションに現れる重みの符号。

```
