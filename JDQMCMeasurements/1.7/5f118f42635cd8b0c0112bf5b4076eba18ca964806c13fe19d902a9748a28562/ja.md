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

不等時の電流-電流相関関数を計算します

$$
\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau) = \frac{1}{N}\sum_{\mathbf{i}}
    \langle[\hat{J}_{\uparrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)+\hat{J}_{\downarrow,\mathbf{i}+\mathbf{r},(\mathbf{r}',a,b)}(\tau)]
    \cdot[\hat{J}_{\uparrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)+\hat{J}_{\downarrow,\mathbf{i},(\mathbf{r}'',c,d)}(0)]\rangle,
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

  * `CC::AbstractArray{C,D}`: 電流相関関数 $\mathcal{J}_{\mathbf{r}}^{(\mathbf{r}',a,b),(\mathbf{r}'',c,d)}(\tau)$ が追加される配列。
  * `b′::Bond{D}`: 電流相関関数の左側に現れる電流演算子を定義するボンド。
  * `b″::Bond{D}`: 電流相関関数の右側に現れる電流演算子を定義するボンド。
  * `tup′::AbstractArray{T,D}`: ボンド `b′` に対応するスピンアップ位置および虚時間依存のホッピング振幅。
  * `tup″::AbstractArray{T,D}`: ボンド `b″` に対応するスピンアップ位置および虚時間依存のホッピング振幅。
  * `tdn′::AbstractArray{T,D}`: ボンド `b′` に対応するスピンダウン位置および虚時間依存のホッピング振幅。
  * `tdn″::AbstractArray{T,D}`: ボンド `b″` に対応するスピンダウン位置および虚時間依存のホッピング振幅。
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
