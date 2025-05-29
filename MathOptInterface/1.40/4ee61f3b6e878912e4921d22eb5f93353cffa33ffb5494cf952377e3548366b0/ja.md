```
ResultStatusCode
```

[`PrimalStatus`](@ref) および [`DualStatus`](@ref) 属性の可能な値の列挙型です。

値は結果ベクトルの解釈方法を示します。

## 値

### [`NO_SOLUTION`](@ref)

結果ベクトルは空です。

### [`FEASIBLE_POINT`](@ref)

結果ベクトルは実行可能な点です。

### [`NEARLY_FEASIBLE_POINT`](@ref)

結果ベクトルは、いくつかの制約の許容範囲が緩和されれば実行可能です。

### [`INFEASIBLE_POINT`](@ref)

結果ベクトルは実行不可能な点です。

### [`INFEASIBILITY_CERTIFICATE`](@ref)

結果ベクトルは実行不可能性の証明書です。

[`PrimalStatus`](@ref) が [`INFEASIBILITY_CERTIFICATE`](@ref) の場合、プライマル結果ベクトルはデュアル実行不可能性の証明書です。

[`DualStatus`](@ref) が [`INFEASIBILITY_CERTIFICATE`](@ref) の場合、デュアル結果ベクトルはプライマル実行不可能性の証明です。

### [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref)

結果は実行不可能性の証明書に対する緩和された基準を満たします。

[`PrimalStatus`](@ref) が [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref) の場合、プライマル結果ベクトルはデュアル実行不可能性の証明書です。

[`DualStatus`](@ref) が [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref) の場合、デュアル結果ベクトルはプライマル実行不可能性の証明です。

### [`REDUCTION_CERTIFICATE`](@ref)

結果ベクトルは不適切な証明書です。詳細については [この論文](https://arxiv.org/abs/1408.4685) を参照してください。

[`PrimalStatus`](@ref) が [`REDUCTION_CERTIFICATE`](@ref) の場合、プライマル結果ベクトルはデュアル問題が不適切であることの証明です。

[`DualStatus`](@ref) が [`REDUCTION_CERTIFICATE`](@ref) の場合、デュアル結果ベクトルはプライマルが不適切であることの証明です。

### [`NEARLY_REDUCTION_CERTIFICATE`](@ref)

結果は不適切な証明書に対する緩和された基準を満たします。

### [`UNKNOWN_RESULT_STATUS`](@ref)

結果ベクトルには未知の解釈を持つ解が含まれています。詳細についてはソルバーログを確認してください。

### [`OTHER_RESULT_STATUS`](@ref)

結果ベクトルには、上記で定義されたステータスのいずれかに該当しない解釈を持つ解が含まれています。詳細についてはソルバーログを確認してください。
