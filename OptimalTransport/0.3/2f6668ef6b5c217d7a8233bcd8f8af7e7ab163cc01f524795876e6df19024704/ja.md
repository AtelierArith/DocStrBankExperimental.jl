```
sinkhorn_divergence(
    μ::AbstractVecOrMat,
    ν::AbstractVecOrMat,
    C,
    ε,
    alg::SinkhornDivergence=SinkhornDivergence(
        SinkhornGibbs(), SymmetricSinkhornGibbs(), SymmetricSinkhornGibbs()
    );
    kwargs...,
)
```

有限離散測度 `μ` と `ν` の間のSinkhornダイバージェンスを、共通のコスト行列 `C`、エントロピー正則化パラメータ `ε`、およびアルゴリズム `alg` に関して計算します。

デフォルトの場合、`regularization = false` のとき、Sinkhornダイバージェンスは [^GPC18] のものであり、次のように計算されます。

$$
\operatorname{S}_{ε}(μ,ν) := \operatorname{W}_{ε}(μ,ν)
- \frac{1}{2}(\operatorname{W}_{ε}(μ,μ) + \operatorname{W}_{ε}(ν,ν)),
$$

ここで、$\operatorname{W}_{ε}$ は次のように定義されます。

$$
\operatorname{W}_{ε}(μ, ν) = \langle C, γ^\star \rangle,
$$

ここで、$γ^\star$ は `μ` と `ν` の間のエントロピー正則化輸送計画です。 `regularization = true` の場合、Sinkhornダイバージェンスは [^FeydyP19] のものであり、上記のように計算され、$\operatorname{W}_{ε}$ は正則化ペナルティを持つエントロピー正則化最適輸送コスト $\operatorname{OT}_{ε}$ に置き換えられます。

項 $\operatorname{W}_{ε}(μ, ν)$ を計算するためのデフォルトのアルゴリズムは `SinkhornGibbs` アルゴリズムです。項 $\operatorname{W}_{ε}(μ, μ)$ および $\operatorname{W}_{ε}(ν, ν)$ については、[^\FeydyP19] の対称固定点反復が使用されます。代わりに、`μ` と `ν` の間の事前計算された最適輸送 `plan` を提供することもできます。

[^GPC18]: Aude Genevay, Gabriel Peyré, Marco Cuturi, Learning Generative Models with Sinkhorn Divergences, Proceedings of the Twenty-First International Conference on Artficial Intelligence and Statistics, (AISTATS) 21, 2018

[^FeydyP19]: Jean Feydy, Thibault Séjourné, François-Xavier Vialard, Shun-ichi Amari, Alain Trouvé, and Gabriel Peyré. Interpolating between optimal transport and mmd using sinkhorn divergences. In The 22nd International Conference on Artificial Intelligence and Statistics, pages 2681–2690. PMLR, 2019.

See also: [`sinkhorn2`](@ref)
