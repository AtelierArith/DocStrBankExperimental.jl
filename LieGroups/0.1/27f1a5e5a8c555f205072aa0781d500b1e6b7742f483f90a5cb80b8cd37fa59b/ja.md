```
LieAlgebra{𝔽, G} <: AbstractManifold{𝔽}
```

リー代数 $\mathfrak g$ を表現します。これは $𝔽$ ベクトル空間で、関連する [`lie_bracket`](@ref) $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$ を持ち、次の条件を満たします。

1. $$
    [X,X] = 0
    $$

    すべての $X ∈ \mathfrak g$ に対して
2. ジャコビの恒等式 $[X, [Y,Z]] = [[X,Y],Z] = [Y, [X,Z]]$ がすべての $X, Y, Z ∈ \mathfrak g$ に対して成り立ちます。

ここで考慮されるリー代数は、[`AbstractLieGroup`](@ref) $\mathcal G$ に関連するものであり、すなわち [`Identity`](@ref) における接空間 $T_{\mathrm{e}}\mathcal G$ であり、これは対応する [`TangentSpace`](@extref `ManifoldsBase.TangentSpace`) の `const` です。

!!! note "リー代数における接ベクトルを表現するための慣習"
    ベクトル場 $\mathcal X: \mathcal G → T\mathcal G$、$X(g) ∈ T_g\mathcal G$ は、次の条件を満たす場合に左不変ベクトル場と呼ばれます。

    $$
    \mathcal X(λ_g(h)) = Dλ_g(h)[\mathcal X(h)], \quad\text{すべての}\quad g, h ∈ \mathcal G,
    $$

    ここで $λ_g: \mathcal G → \mathcal G$ は $g$ による左乗法です。したがって、$X ∈ \mathfrak g$ が与えられると、$\mathcal X$ はすでに決定されます。なぜなら、$\mathcal X(g) = Dλ_g(e)[X]$ だからです。参照 [HilgertNeeb:2012; Definition 9.1.7](@cite)。

    `LieGroups.jl` 全体で、リー群の点における接ベクトルを対応するリー代数の要素として保存するために、この左不変の慣習を使用します。


# コンストラクタ

```
LieAlgebra(G::AbstractLieGroup)
```

[`AbstractLieGroup`](@ref) `G` に属するリー代数を返します。
