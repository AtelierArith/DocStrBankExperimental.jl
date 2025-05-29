```
probabilities_and_outcomes(
    [est::ProbabilitiesEstimator], o::OutcomeSpace, x::Array_or_SSSet
) → (p::Probabilities, Ω)
```

入力データ `x` に基づいて、[`OutcomeSpace`](@ref) `o` によって定義された可能な結果の集合 `Ω` に対する確率分布を推定します。確率は、デフォルトで [`RelativeAmount`](@ref) を使用する指定された確率推定器 `est` に従って推定されます。

入力データは通常、`Array` または `StateSpaceSet`（略して `SSSet`）です。詳細は [Input data for ComplexityMeasures.jl](@ref input_data) を参照してください。構成オプションは、選択した結果空間と確率推定器に対する引数として常に指定されます。

最初の要素が確率を含むベクトルのような [`Probabilities`](@ref) インスタンスであり、2 番目の要素 `Ω` が確率に対応する結果であるタプルを返します。すなわち、`p[i]` は結果 `Ω[i]` の確率です。

結果は実際には `p` に含まれており、`p` に対して [`outcomes`](@ref) 関数を使用して取得できます。`probabilities_and_outcomes` は、後方互換性のために両方を返します。

```
probabilities_and_outcomes(
    [est::ProbabilitiesEstimator], counts::Counts
) → (p::Probabilities, Ω)
```

指定された [`ProbabilitiesEstimator`](@ref) `est` を使用して、事前に計算された `counts` から確率を推定します。

## 説明

確率は次のように計算されます。

1. 提供された [`OutcomeSpace`](@ref) `o` によって指定された有限の結果集合 `Ω` に `x` を離散化/エンコードします。
2. 各結果 `Ωᵢ ∈ Ω` に対して、離散化されたデータポイントの中でどれだけ頻繁に現れるかを示すカウント、または `sum(Ωᵢ for Ωᵢ in Ω) == 1` となるような事前に正規化された確率を割り当てます。

擬似カウントを生成する結果空間（例： [`PowerSpectrum`](@ref)）では、これらの擬似カウントは単に確率として扱われ、直接返されます（つまり、`est` は無視されます）。カウントベースの結果空間（[`OutcomeSpace`](@ref) のドキュメントを参照）では、確率はカウントから推定されます（最初のシグネチャ）。

## 観測された確率とすべての確率

パフォーマンスの最適化により、返される確率に `0` が含まれるかどうかは結果空間によって異なります。例えば、[`ValueBinning`](@ref) では `0` はスキップされますが、[`PowerSpectrum`](@ref) では `0` はスキップされず、無料で得られます。

ゼロ確率も返されることを保証するには [`allprobabilities_and_outcomes`](@ref) を使用してください（遅くなる可能性があります）。
