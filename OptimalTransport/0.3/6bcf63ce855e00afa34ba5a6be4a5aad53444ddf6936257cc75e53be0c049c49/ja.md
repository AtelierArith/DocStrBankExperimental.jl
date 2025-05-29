```
sinkhorn_divergence(
    μ,
    ν,
    Cμν,
    Cμ,
    Cν,
    ε,
    alg::SinkhornDivergence=SinkhornDivergence(
        SinkhornGibbs(), SymmetricSinkhornGibbs(), SymmetricSinkhornGibbs()
    );
    kwargs...,
)
```

有限離散測度 `μ` と `ν` の間のSinkhornダイバージェンスを、事前に計算されたコスト行列 `Cμν`、`Cμμ` および `Cνν`、エントロピー正則化パラメータ `ε` およびアルゴリズム `alg` に関して計算します。

`μ` と `ν` の間の事前計算された最適輸送 `plan` を提供することもできます。

参照: [`sinkhorn2`](@ref), [`sinkhorn_divergence`](@ref)
