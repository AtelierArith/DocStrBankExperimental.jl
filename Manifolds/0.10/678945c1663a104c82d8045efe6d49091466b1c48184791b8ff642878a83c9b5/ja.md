```
convert(::Type{HyperboloidTangentVector}, p::PoincareBallPoint, X::PoincareBallTangentVector)
convert(::Type{AbstractVector}, p::PoincareBallPoint, X::PoincareBallTangentVector)
```

[`PoincareBallTangentVector`](@ref) `X` を `p` における接空間から [`HyperboloidTangentVector`](@ref) に変換するには、等長写像のプッシュフォワードを計算します。cf. [`convert(::Type{HyperboloidPoint}, p::PoincareBallPoint)`](@ref)。

プッシュフォワード $π_*(p)$ は $ℝ^n$ から $ℝ^{n+1}$ の部分空間に写像します。式は次のようになります。

$$
π_*(p)[X] = \begin{pmatrix}
    \frac{2X_1}{1-\lVert p \rVert^2} + \frac{4}{(1-\lVert p \rVert^2)^2}⟨X,p⟩p_1\\
    ⋮\\
    \frac{2X_n}{1-\lVert p \rVert^2} + \frac{4}{(1-\lVert p \rVert^2)^2}⟨X,p⟩p_n\\
    \frac{4}{(1-\lVert p \rVert^2)^2}⟨X,p⟩
\end{pmatrix}.
$$
