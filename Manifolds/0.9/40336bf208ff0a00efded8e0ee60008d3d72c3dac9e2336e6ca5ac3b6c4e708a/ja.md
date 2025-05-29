```
convert(
    ::Type{PoincareBallTVector},
    p::PoincareHalfSpacePoint,
    X::PoincareHalfSpaceTVector
)
```

[`PoincareHalfSpaceTVector`](@ref) `X` を `p` での [`PoincareBallTVector`](@ref) に変換するには、ポアンカレ半空間からポアンカレ球への等距離写像 $π$ のプッシュフォワード $π_*(p)[X]$ を計算します。これは [`convert(::Type{PoincareBallPoint}, ::PoincareHalfSpacePoint)`](@ref) を参照してください。

式は次のようになります。

$$
π_*(p)[X] =
\frac{1}{\lVert \tilde p\rVert^2 + (1+p_n)^2}
\begin{pmatrix}
2X_1\\
⋮\\
2X_{n-1}\\
2⟨X,p⟩
\end{pmatrix}
-
\frac{2}{(\lVert \tilde p\rVert^2 + (1+p_n)^2)^2}
\begin{pmatrix}
2p_1(⟨X,p⟩+X_n)\\
⋮\\
2p_{n-1}(⟨X,p⟩+X_n)\\
(\lVert p \rVert^2-1)(⟨X,p⟩+X_n)
\end{pmatrix}
$$

ここで、$\tilde p = \begin{pmatrix}p_1\\⋮\\p_{n-1}\end{pmatrix}$ です。
