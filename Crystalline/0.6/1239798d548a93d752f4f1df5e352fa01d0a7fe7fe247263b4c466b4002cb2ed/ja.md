```
primitivize(v::AbstractVec, cntr::Char)  -->  v′::typeof(v)
```

従来の座標ベクトル `v` を標準の原始基底（中心タイプ `cntr` によって指定）に変換し、原始座標ベクトル `v′` を返します。

基底変換行列 $\mathbf{P}$ （例えば [`Bravais.primitivebasismatrix`](@ref) によって返されるもの）は、直接座標ベクトル ([`RVec`](@ref)) を $\mathbf{r}' = \mathbf{P}^{-1}\mathbf{r}$ のように変換しますが、逆数座標 ([`KVec`](@ref)) は $\mathbf{k}' = \mathbf{P}^{\text{T}}\mathbf{k}$ のように変換します [^ITA6]。また、基底を変換することとベクトルの座標を変換することの違いにも注意してください。

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th edition (2016):      Secs. 1.5.1.2 and 1.5.2.1.
