```
greens!(
    G::AbstractArray{C,D},
    a::Int, b::Int, unit_cell::UnitCell{D}, lattice::Lattice{D},
    G_τ0::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Number, T<:Number}
```

翻訳対称性で平均化された不均一時間グリーン関数を測定します

$$
G_{\sigma,\mathbf{r}}^{a,b}(\tau)=\frac{1}{N}\sum_{\mathbf{i}}G_{\sigma,\mathbf{i}+\mathbf{r},\mathbf{i}}^{a,b}(\tau,0)
=\frac{1}{N}\sum_{\mathbf{i}}\langle\hat{\mathcal{T}}\hat{a}_{\sigma,\mathbf{i}+\mathbf{r}}^{\phantom{\dagger}}(\tau)\hat{b}_{\sigma,\mathbf{i}}^{\dagger}(0)\rangle,
$$

結果は `G` に追加されます。

# フィールド

  * `G::AbstractArray{C,D}`: グリーン関数 $G_{\sigma,\mathbf{r}}^{a,b}(\tau)$ が書き込まれる配列。
  * `a::Int`: 単位格子内の軌道種を指定するインデックス。
  * `b::Int`: 単位格子内の軌道種を指定するインデックス。
  * `unit_cell::UnitCell{D}`: 単位格子を定義します。
  * `lattice::Lattice{D}`: 有限格子のサイズを指定します。
  * `G_τ0::AbstractMatrix{T}`: 行列 $G(\tau,0).$
  * `sgn=one(C)`: DQMCシミュレーションに現れる重みの符号。
