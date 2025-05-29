```
AnovaResult{M, T, N}
```

`anova`の返されたオブジェクト。

  * `M`は`NestedModels`または`FullModel`です。
  * `T`は`GoodnessOfFit`のサブタイプであり、`FTest`または`LRT`のいずれかです。
  * `N`はパラメータの長さです。

# フィールド

  * `anovamodel`: [`NestedModels`](@ref)、[`MixedAovModels`](@ref)、または[`FullModel`](@ref)。
  * `dof`: モデルまたは予測子の自由度。
  * `deviance`: テスト統計量を計算するための逸脱値。詳細については[`deviance`](@ref)を参照してください。
  * `teststat`: テスト統計量の値。
  * `pval`: テスト統計量のp値。
  * `otherstat`: 追加の統計を含む`NamedTuple`。

# コンストラクタ

```
AnovaResult(
        anovamodel::M,
        ::Type{T},
        dof::NTuple{N, Int},
        deviance::NTuple{N, Float64},
        teststat::NTuple{N, Float64},
        pval::NTuple{N, Float64},
        otherstat::NamedTuple
) where {N, M <: AnovaModel{<: RegressionModel, N}, T <: GoodnessOfFit}
```
