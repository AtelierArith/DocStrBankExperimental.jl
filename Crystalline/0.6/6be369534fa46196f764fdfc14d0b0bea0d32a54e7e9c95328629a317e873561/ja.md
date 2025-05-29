```
transform(v::AbstractVec, P::AbstractMatrix)  -->  v′::typeof(v)
```

元の座標ベクトル `v` から変換された座標ベクトル `v′` を、基底変換行列 `P` を使用して返します。

基底変換行列 $\mathbf{P}$ は、直接座標ベクトル（`RVec`）を $\mathbf{r}' = \mathbf{P}^{-1}\mathbf{r}$ のように変換しますが、逆数座標（`KVec`）は $\mathbf{k}' = \mathbf{P}^{\mathrm{T}}\mathbf{k}$ のように変換します [^ITA6]

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th edition (2016):      Secs. 1.5.1.2 and 1.5.2.1.
