```
rand(M::SymplecticStiefel; vector_at=nothing, σ = 1.0)
```

点 $p ∈ \mathrm{SpSt}(2n, 2k)$ のランダムな点を生成するか、`vector_at` が点 $p ∈ \mathrm{Sp}(2n)$ に設定されている場合は、ランダムな接ベクトル $X ∈ T_p\mathrm{SpSt}(2n, 2k)$ を生成します。

$$
\mathrm{SpSt}(2n, 2k)
$$

上のランダムな点は、まずシンプレクティック多様体 $\mathrm{Sp}(2n)$ 上のランダムな点を生成し、その後 [`canonical_project`](@ref) $π_{\mathrm{SpSt}(2n, 2k)}$ を使用してシンプレクティック・スティーフェル多様体に射影することで見つけられます。すなわち、$p = π_{\mathrm{SpSt}(2n, 2k)}(p_{\mathrm{Sp}})$ です。

$$
T_p\mathrm{SpSt}(2n, 2k)
$$

におけるランダムな接ベクトルを生成するために、このコードは [`SymplecticStiefel`](@ref) の第二接ベクトル空間のパラメータ化を利用します。任意の $X ∈ T_p\mathrm{SpSt}(2n, 2k)$ は $X = pΩ_X + p^sB_X$ と書くことができます。したがって、$p$ におけるランダムな接ベクトルを生成するために、この関数は $B_X = 0$ と設定し、Frobenius ノルムが `σ` のランダムなハミルトニアン行列 $Ω_X ∈ \mathfrak{sp}(2n,F)$ を生成し、$X = pΩ_X$ を返します。
