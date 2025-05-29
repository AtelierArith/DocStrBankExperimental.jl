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

不等時間ボンド-ボンド相関関数を計算します

$$
\begin{align*}
\mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau) =
    & \frac{1}{N}\sum_{\mathbf{i}} \langle[\hat{B}_{\uparrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)+\hat{B}_{\downarrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)]
                                   \cdot[\hat{B}_{\uparrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)+\hat{B}_{\downarrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)]\rangle
\end{align*}
$$

ここで、

$$
\hat{B}_{\sigma,\mathbf{i},(\mathbf{r},a,b)}
    = \hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}\hat{b}_{\sigma,\mathbf{i}}^{\phantom{\dagger}}
    + \hat{b}_{\sigma,\mathbf{i}}^{\dagger}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}
$$

はボンド演算子です。

# フィールド

  * `BB::AbstractArray{C,D}`: ボンド相関関数 $\mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau)$ が追加される配列。
  * `b′::Bond{D}`: ボンド相関関数の左側に現れるボンド演算子を定義するボンド。
  * `b″::Bond{D}`: ボンド相関関数の右側に現れるボンド演算子を定義するボンド。
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
