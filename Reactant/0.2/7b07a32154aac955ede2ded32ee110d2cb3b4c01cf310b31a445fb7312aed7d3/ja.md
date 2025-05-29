```
with_config(f; kwargs...)
```

関数 `f` を動的スコープ内で実行し、このスコープ内のすべての config の使用は提供された値を使用します。

# 拡張ヘルプ

## 設定オプション

### 降下

  * `lower_partialsort_to_approx_top_k`: `partialsort` と `partialsortperm` を `Ops.approx_top_k` に降下させるかどうか。XLA は `fallback_approx_top_k_lowering` が `true` に設定されていない限り、TPU のために `ApproxTopK` の降下のみをサポートします。
  * `fallback_approx_top_k_lowering`: XLA バックエンドが `ApproxTopK` をサポートしていない場合に `Ops.approx_top_k` を `stablehlo.top_k` に降下させるかどうか。デフォルトは `true` です。

### DotGeneral

  * `dot_general_algorithm`: `stablehlo.dot_general` のアルゴリズムプリセット。`nothing`、[`DotGeneralAlgorithm`](@ref) または [`DotGeneralAlgorithmPreset`](@ref) のいずれかです。デフォルトは `DotGeneralAlgorithmPreset.DEFAULT` です。
  * `dot_general_precision`: `stablehlo.dot_general` の精度。`nothing` または [`PrecisionConfig`](@ref) のいずれかです。デフォルトは `PrecisionConfig.DEFAULT` です。
  * `convolution_precision`: `stablehlo.convolution` の精度。`nothing` または [`PrecisionConfig`](@ref) のいずれかです。デフォルトは `PrecisionConfig.DEFAULT` です。

```
