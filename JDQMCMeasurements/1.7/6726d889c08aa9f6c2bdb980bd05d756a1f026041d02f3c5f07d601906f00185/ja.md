```
pair_correlation!(
    P::AbstractArray{C,D},
    b″::Bond{D}, b′::Bond{D}, unit_cell::UnitCell{D}, lattice::Lattice{D},
    Gup_τ0::AbstractMatrix{T}, Gdn_τ0::AbstractMatrix{T},
    sgn=one(C)
) where {D, C<:Number, T<:Number}
```

不等時ペア相関関数を計算します

$$
\mathcal{P}_{\mathbf{r}}^{(a,b,r''),(c,d,r')}(\tau)=\frac{1}{N}\sum_{\mathbf{i}}\mathcal{P}_{\mathbf{i}+\mathbf{r},\mathbf{i}}^{(a,b,r''),(c,d,r')}(\tau,0)
=\frac{1}{N}\sum_{\mathbf{i}}\langle\hat{\Delta}_{\mathbf{i}+\mathbf{r},a,b,\mathbf{r}''}(\tau)\hat{\Delta}_{\mathbf{i},c,d,\mathbf{r}'}^{\dagger}(0)\rangle,
$$

ここで、ボンド `b″` はペア生成演算子を定義します

$$
\hat{\Delta}_{\mathbf{i},a,b,\mathbf{r}''}^{\dagger}=\hat{a}_{\uparrow,\mathbf{i}+\mathbf{r}''}^{\dagger}\hat{b}_{\downarrow,\mathbf{i}}^{\dagger},
$$

そして、ボンド `b′` はペア生成演算子を定義します

$$
\hat{\Delta}_{\mathbf{i},c,d,\mathbf{r}'}^{\dagger}=\hat{c}_{\uparrow,\mathbf{i}+\mathbf{r}'}^{\dagger}\hat{d}_{\downarrow,\mathbf{i}}^{\dagger}.
$$

# フィールド

  * `P::AbstractArray{C,D}`: ペア相関関数 $\mathcal{P}_{\mathbf{r}}^{(a,b,r''),(c,d,r')}(\tau)$ が追加される配列。
  * `b″::Bond{D}`: ペア相関関数に現れるペア消滅演算子を定義するボンド。
  * `b′::Bond{D}`: ペア相関関数に現れるペア生成演算子を定義するボンド。
  * `unit_cell::UnitCell{D}`: 単位セルを定義します。
  * `lattice::Lattice{D}`: 有限格子のサイズを指定します。
  * `Gup_τ0::AbstractMatrix{T}`: 行列 $G_{\uparrow}(\tau,0).$
  * `Gdn_τ0::AbstractMatrix{T}`: 行列 $G_{\downarrow}(\tau,0).$
  * `sgn=one(C)`: DQMCシミュレーションに現れる重みの符号。
