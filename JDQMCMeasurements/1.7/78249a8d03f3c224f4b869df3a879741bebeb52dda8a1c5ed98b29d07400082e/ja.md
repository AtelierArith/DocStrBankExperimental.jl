```
density_correlation!(
    DD::AbstractArray{C,D},
    a::Int, b::Int, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gσ_τ0::AbstractMatrix{T}, Gσ_0τ::AbstractMatrix{T},
    Gσ_ττ::AbstractMatrix{T}, Gσ′_00::AbstractMatrix{T},
    σ::Int, σ′::Int, sgn=one(C)
) where {D, C<:Number, T<:Number}
```

スピン分解された不等時密度相関関数を計算します

$$
\begin{align*}
    \mathcal{D}_{\mathbf{r}}^{(a,\sigma),(b,\sigma')}(\tau)
            = \frac{1}{N}\sum_{\mathbf{i}} & \mathcal{D}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{(a,\sigma),(b,\sigma')}(\tau,0) \\
            = \frac{1}{N}\sum_{\mathbf{i}} & \langle\hat{n}_{\sigma,a,\mathbf{i}+\mathbf{r}}(\tau)\hat{n}_{\sigma',b,\mathbf{r}}(0)\rangle,
\end{align*}
$$

ここで、$\hat{n}_{\sigma', b,\mathbf{i}} = \hat{b}^\dagger_{\sigma', \mathbf{i}} \hat{b}_{\sigma, \mathbf{i}}$ は、単位セル $\mathbf{i}$ における軌道 $b$ のスピン $\sigma'$ を持つ電子の数演算子であり、結果は配列 `DD` に追加されます。

# フィールド

  * `DD::AbstractArray{C,D}`: スピン分解された密度相関 $\mathcal{D}_{\mathbf{r}}^{(a,\sigma),(b,\sigma')}(\tau)$ が追加される配列。
  * `a::Int`: 単位セル内の軌道種を指定するインデックス。
  * `b::Int`: 単位セル内の軌道種を指定するインデックス。
  * `unit_cell::UnitCell{D}`: 単位セルを定義します。
  * `lattice::Lattice{D}`: 有限格子のサイズを指定します。
  * `Gσ_τ0::AbstractMatrix{T}`: 行列 $G_{\sigma}(\tau,0).$
  * `Gσ_0τ::AbstractMatrix{T}`: 行列 $G_{\sigma}(0,\tau).$
  * `Gσ_ττ::AbstractMatrix{T}`: 行列 $G_{\sigma}(\tau,\tau).$
  * `Gσ′_00::AbstractMatrix{T}`: 行列 $G_{\sigma'}(0,0).$
  * `σ::Int`: $\langle \hat{n} \rangle_{\sigma,a,\mathbf{i}+\mathbf{r}}$ 密度演算子に現れる電子スピン。
  * `σ′::Int`: $\langle \hat{n} \rangle_{\sigma',b,\mathbf{i}}$ 密度演算子に現れる電子スピン。
  * `sgn=one(C)`: DQMC シミュレーションに現れる重みの符号。
