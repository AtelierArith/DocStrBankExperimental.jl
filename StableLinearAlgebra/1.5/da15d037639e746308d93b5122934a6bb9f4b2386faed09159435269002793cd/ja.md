```
LDR{T<:Number, E<:Real} <: Factorization{T}
```

正方行列 $A$ の行列因子分解 $A = L D R$ を表します。ここで、$L$ は単位行列、$D$ は厳密に正の実数の対角行列、$R$ は $|\det R| = 1$ となるように定義されます。

この因子分解は、列ピボットQR分解 $A P = Q R'$ に基づいており、次のようになります。

$$
\begin{align*}
L &:= Q \\
D &:= \vert \textrm{diag}(R') \vert \\
R &:= \vert \textrm{diag}(R') \vert^{-1} R' P^T\\
\end{align*}
$$

# フィールド

  * `L::Matrix{T}`: [`LDR`](@ref) 因子分解における左の単位行列 $L$。
  * `d::Vector{E}`: [`LDR`](@ref) 因子分解における対角行列 $D$ を表すベクトル。
  * `R::Matrix{T}`: [`LDR`](@ref) 因子分解における右の行列 $R$。
