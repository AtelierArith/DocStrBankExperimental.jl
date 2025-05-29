```
OptISTA(A; AHA=A'*A, reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho=0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))))
OptISTA( ; AHA=,     reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho=0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))))
```

は、前方演算子 `A` または正規演算子 `AHA` のための `OptISTA` オブジェクトを作成します。OptISTA は FISTA よりも最悪の場合の境界が 2 倍良好ですが、実際のパフォーマンスはアプリケーションによって異なります。FISTA と比較して、画像のサイズと同じ 2 つの追加の中間変数を保存します。

参考文献:

  * Uijeong Jang, Shuvomoy Das Gupta, Ernest K. Ryu, "Computer-Assisted Design of Accelerated Composite Optimization Methods: OptISTA," arXiv:2305.15704, 2023, [https://arxiv.org/abs/2305.15704]

# 必須引数

  * `A`                                                 - 前方演算子

または

  * `AHA`                                               - 正規演算子（キーワード引数として）

# オプションのキーワード引数

  * `AHA`                                               - `A` が提供されている場合、正規演算子はオプションです
  * `reg::AbstractParameterizedRegularization`          - 正則化項
  * `normalizeReg::AbstractRegularizationNormalization` - 正則化正規化スキーム; オプションは `NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `rho::Real`                                         - 勾配ステップのステップサイズ; デフォルトは `0.95 / max_eigenvalue` で、パワー反復によって決定されます。
  * `theta::Real`                                       - 予測子-修正子ステップのパラメータ
  * `relTol::Real`                                      - 停止基準の許容誤差
  * `iterations::Int`                                   - 最大反復回数
  * `verbose::Bool`                                     - 各反復で残差を印刷

[`createLinearSolver`](@ref) や [`solve!`](@ref) も参照してください。
