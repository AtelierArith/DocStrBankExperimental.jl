```
CGNR(A; AHA = A' * A, reg = L2Regularization(zero(real(eltype(AHA)))), normalizeReg = NoNormalization(), iterations = 10, relTol = eps(real(eltype(AHA))))
CGNR( ; AHA = ,       reg = L2Regularization(zero(real(eltype(AHA)))), normalizeReg = NoNormalization(), iterations = 10, relTol = eps(real(eltype(AHA))))
```

は、前方演算子 `A` または正規演算子 `AHA` のための `CGNR` オブジェクトを作成します。

# 必要な引数

  * `A`                                                 - 前方演算子

または

  * `AHA`                                               - 正規演算子（キーワード引数として）

# オプションのキーワード引数

  * `AHA`                                               - `A` が供給されている場合、正規演算子はオプションです
  * `reg::AbstractParameterizedRegularization`          - 正則化項; 正則化項のベクトルも可能です
  * `normalizeReg::AbstractRegularizationNormalization` - 正則化正規化スキーム; オプションは `NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()` です
  * `iterations::Int`                                   - 最大反復回数
  * `relTol::Real`                                      - 停止基準の許容誤差

詳細は [`createLinearSolver`](@ref), [`solve!`](@ref) を参照してください。
