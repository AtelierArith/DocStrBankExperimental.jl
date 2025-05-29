```
DissipationMatrixWintersEtal()
```

Winters et al. (2017) による Roe のようなエントロピー安定行列散逸演算子を作成します。この演算子は、エントロピー保存の二点フラックス関数（例: [`flux_ranocha`](@ref) または [`flux_chandrashekar`](@ref)）と一緒に使用する必要があり、エントロピー安定な表面フラックスを生成します。表面フラックス関数は次のように初期化できます:

```julia
flux_es = FluxPlusDissipation(flux_ec, DissipationMatrixWintersEtal())
```

1D および 2D の実装は [Atum.jl ライブラリ](https://github.com/mwarusz/Atum.jl/blob/c7ed44f2b7972ac726ef345da7b98b0bda60e2a3/src/balancelaws/euler.jl#L198) から適応されています。3D の実装は [FLUXO ライブラリ](https://github.com/project-fluxo/fluxo) から適応されています。

行列散逸演算子の導出については、次を参照してください:

  * A. R. Winters, D. Derigs, G. Gassner, S. Walch, 高マッハ数理想 MHD および圧縮性オイラーシミュレーションのための一意に定義されたエントロピー安定行列散逸演算子 (2017)。計算物理学ジャーナル。 [DOI: 10.1016/j.jcp.2016.12.006](https://doi.org/10.1016/j.jcp.2016.12.006).
