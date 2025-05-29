```
rand(::SymplecticStiefel; vector_at=nothing, σ::Real=1.0)
```

$$
\mathrm{Sp}(2n)
$$

上のランダムな点を生成するか、`vector_at`が点$p \in \mathrm{Sp}(2n)$に設定されている場合は、ランダムな接ベクトル$X \in T_p\mathrm{Sp}(2n)$を生成します。

$$
\mathrm{Sp}(2n)
$$

上のランダムな点は、ノルム`σ`を持つランダムなハミルトン行列$Ω \in \mathfrak{sp}(2n,F)$を生成し、それをケイリー変換を適用してシンプレクティック行列に変換することによって構築されます。

$$
  \operatorname{cay}: \mathfrak{sp}(2n,F) → \mathrm{Sp}(2n),
  \ \Omega \mapsto (I - \Omega)^{-1}(I + \Omega).
$$

$$
T_p\mathrm{Sp}(2n)
$$

内のランダムな接ベクトルを生成するために、このコードは[`SymplecticMatrices`](@ref)の第二接ベクトル空間のパラメータ化を使用します。最初に、`S = randn(2n, 2n)`によってランダムな対称行列$S$を生成し、次にそれを`S = S + S'`として対称化します。その後、$S$はフロベニウスノルムが`σ`になるように正規化され、`X = pJS`が返されます。ここで、`J`は[`SymplecticElement`](@ref)です。
