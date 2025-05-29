```
ResultStatusCode
```

`PrimalStatus` および `DualStatus` 属性の可能な値の列挙型です。値は結果ベクトルの解釈方法を示します。

  * `NO_SOLUTION`: 結果ベクトルは空です。
  * `FEASIBLE_POINT`: 結果ベクトルは実行可能な点です。
  * `NEARLY_FEASIBLE_POINT`: 結果ベクトルは、いくつかの制約の許容範囲が緩和されれば実行可能です。
  * `INFEASIBLE_POINT`: 結果ベクトルは実行不可能な点です。
  * `INFEASIBILITY_CERTIFICATE`: 結果ベクトルは実行不可能性の証明書です。`PrimalStatus` が `INFEASIBILITY_CERTIFICATE` の場合、プライマル結果ベクトルはデュアルの実行不可能性の証明書です。`DualStatus` が `INFEASIBILITY_CERTIFICATE` の場合、デュアル結果ベクトルはプライマルの実行不可能性の証明です。
  * `NEARLY_INFEASIBILITY_CERTIFICATE`: 結果は実行不可能性の証明書に対する緩和された基準を満たします。
  * `REDUCTION_CERTIFICATE`: 結果ベクトルは不適切な証明書です。詳細については [この論文](https://arxiv.org/abs/1408.4685) を参照してください。`PrimalStatus` が `REDUCTION_CERTIFICATE` の場合、プライマル結果ベクトルはデュアル問題が不適切であることの証明です。`DualStatus` が `REDUCTION_CERTIFICATE` の場合、デュアル結果ベクトルはプライマルが不適切であることの証明です。
  * `NEARLY_REDUCTION_CERTIFICATE`: 結果は不適切な証明書に対する緩和された基準を満たします。
  * `UNKNOWN_RESULT_STATUS`: 結果ベクトルには未知の解釈を持つ解が含まれています。
  * `OTHER_RESULT_STATUS`: 結果ベクトルには上記のいずれかのステータスでカバーされていない解釈を持つ解が含まれています。
