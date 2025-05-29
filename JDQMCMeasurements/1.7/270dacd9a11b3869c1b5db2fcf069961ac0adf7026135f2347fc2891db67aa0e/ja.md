```
bond_correlation!(
    BB::AbstractArray{C,D},
    b′::Bond{D}, b″::Bond{D}, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gσ′_τ0::AbstractMatrix{T}, Gσ′_0τ::AbstractMatrix{T},
    Gσ′_ττ::AbstractMatrix{T}, Gσ″_00::AbstractMatrix{T},
    σ′::Int, σ″::Int, sgn=one(C)
) where {D, C<:Number, T<:Number}
```

スピン分解された非等時ボンド-ボンド相関関数を計算します

$$
\begin{align*}
    \mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)
        = \frac{1}{N}\sum_{\mathbf{i}} & \mathcal{B}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau,0)\\
        =\frac{1}{N}\sum_{\mathbf{i}} & \langle\hat{B}_{\sigma',\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)\hat{B}_{\sigma'',\mathbf{i},(\mathbf{r}'',c,d)}(0)\rangle,
\end{align*}
$$

ここで

$$
\begin{align*}
    \hat{B}_{\sigma,\mathbf{i},(\mathbf{r},a,b)}
        & = \hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}\hat{b}_{\sigma,\mathbf{i}}^{\phantom{\dagger}}+\hat{b}_{\sigma,\mathbf{i}}^{\dagger}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}\\
        & = -\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}\hat{b}_{\sigma,\mathbf{i}}^{\dagger}-\hat{b}_{\sigma,\mathbf{i}}^{\phantom{\dagger}}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}
\end{align*}
$$

はボンド演算子です。

# フィールド

  * `BB::AbstractArray{C,D}`: スピン分解されたボンド相関関数 $\mathcal{B}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)$ が追加される配列。
  * `b′::Bond{D}`: ボンド相関関数の左側に現れるボンド演算子を定義するボンド。
  * `b″::Bond{D}`: ボンド相関関数の右側に現れるボンド演算子を定義するボンド。
  * `unit_cell::UnitCell{D}`: 単位セルを定義します。
  * `lattice::Lattice{D}`: 有限格子のサイズを指定します。
  * `Gσ′_τ0::AbstractMatrix{T}`: 行列 $G_{\sigma'}(\tau,0).$
  * `Gσ′_0τ::AbstractMatrix{T}`: 行列 $G_{\sigma'}(0,\tau).$
  * `Gσ′_ττ::AbstractMatrix{T}`: 行列 $G_{\sigma'}(\tau,\tau).$
  * `Gσ″_00::AbstractMatrix{T}`: 行列 $G_{\sigma''}(0,0).$
  * `σ′::Int`: $\hat{B}_{\sigma',\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}$ ボンド演算子に現れる電子スピン。
  * `σ″::Int`: $\hat{B}_{\sigma'',\mathbf{i},(\mathbf{r}'',c,d)}$ ボンド演算子に現れる電子スピン。
  * `sgn=one(C)`: DQMCシミュレーションに現れる重みの符号。
