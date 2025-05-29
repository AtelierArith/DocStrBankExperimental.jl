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

スピン分解された非等時電流-電流相関関数を計算します

$$
\begin{align*}
\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)
    & = \frac{1}{N}\sum_{\mathbf{i}}\mathcal{J}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau,0)\\
    & = \frac{1}{N}\sum_{\mathbf{i}}\langle\hat{J}_{\sigma',\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)\hat{J}_{\sigma'',\mathbf{i},(\mathbf{r}'',c,d)}(0)\rangle,
\end{align*}
$$

ここで、スピン分解された電流演算子は次のように与えられます

$$
\begin{align*}
    \hat{J}_{\sigma,\mathbf{i},(\mathbf{r},a,b)}
        & = -{\rm i}(t_{\sigma,\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b} \hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\dagger}\hat{b}_{\sigma,\mathbf{i}} - t_{\sigma,\mathbf{i}, \mathbf{i}+\mathbf{r}}^{b,a} \hat{b}_{\sigma,\mathbf{i}}^{\dagger}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}})\\
\end{align*}
$$

および $t_{\sigma,\mathbf{i}, \mathbf{i}+\mathbf{r}}^{b,a} = \big( t_{\sigma,\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b} \big)^*$.

# フィールド

  * `CC::AbstractArray{C,D}`: スピン分解された電流相関関数 $\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b,\sigma'),(\mathbf{r}'',c,d,\sigma'')}(\tau)$ が追加される配列。
  * `b′::Bond{D}`: 電流相関関数の左側に現れる電流演算子を定義するボンド。
  * `b″::Bond{D}`: 電流相関関数の右側に現れる電流演算子を定義するボンド。
  * `t′::AbstractArray{T,D}`: ボンド `b′` に関連する位置および虚時間依存のホッピング振幅。
  * `t″::AbstractArray{T,D}`: ボンド `b″` に関連する位置および虚時間依存のホッピング振幅。
  * `unit_cell::UnitCell{D}`: 単位セルを定義します。
  * `lattice::Lattice{D}`: 有限格子のサイズを指定します。
  * `Gσ′_τ0::AbstractMatrix{T}`: 行列 $G_{\sigma'}(\tau,0).$
  * `Gσ′_0τ::AbstractMatrix{T}`: 行列 $G_{\sigma'}(0,\tau).$
  * `Gσ′_ττ::AbstractMatrix{T}`: 行列 $G_{\sigma'}(\tau,\tau).$
  * `Gσ″_00::AbstractMatrix{T}`: 行列 $G_{\sigma''}(0,0).$
  * `σ′::Int`: 左側の電流演算子に現れる電子スピン。
  * `σ″::Int`: 右側の電流演算子に現れる電子スピン。
  * `sgn=one(C)`: DQMCシミュレーションに現れる重みの符号。
