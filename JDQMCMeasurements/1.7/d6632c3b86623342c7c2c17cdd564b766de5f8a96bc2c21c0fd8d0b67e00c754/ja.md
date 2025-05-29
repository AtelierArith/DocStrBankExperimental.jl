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

不均一時間密度-密度（電荷）相関関数を計算します

$$
\begin{align*}
\mathcal{D}_{\mathbf{r}}^{a,b}(\tau)
    & = \frac{1}{N}\sum_{\mathbf{i}} \mathcal{D}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b}(\tau,0)\\
    & = \frac{1}{N}\sum_{\mathbf{i}} \langle \hat{n}_{a,\mathbf{i} + \mathbf{r}}(\tau)\hat{n}_{b,\mathbf{i}}(0) \rangle,
\end{align*}
$$

ここで、$\hat{n}_{b,\mathbf{i}} = (\hat{n}_{\uparrow, b, \mathbf{i}} + \hat{n}_{\downarrow, b, \mathbf{i}})$ および $\hat{n}_{\sigma, b,\mathbf{i}} = \hat{b}^\dagger_{\sigma, \mathbf{i}} \hat{b}_{\sigma, \mathbf{i}}$ は、単位セル $\mathbf{i}$ における軌道 $b$ のスピン $\sigma$ を持つ電子の数演算子であり、結果は配列 `DD` に追加されます。

# フィールド

  * `DD::AbstractArray{C,D}`: 密度相関関数 $\mathcal{D}_{\mathbf{r}}^{a,b}(\tau)$ が追加される配列。
  * `a::Int`: 単位セル内の軌道種を指定するインデックス。
  * `b::Int`: 単位セル内の軌道種を指定するインデックス。
  * `unit_cell::UnitCell{D}`: 単位セルを定義します。
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

```
