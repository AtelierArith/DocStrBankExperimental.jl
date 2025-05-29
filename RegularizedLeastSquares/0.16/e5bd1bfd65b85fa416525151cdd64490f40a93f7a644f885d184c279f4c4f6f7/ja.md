```
FISTA(A; AHA=A'*A, reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho = 0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))), restart = :none)
FISTA( ; AHA=,     reg=L1Regularization(zero(real(eltype(AHA)))), normalizeReg=NoNormalization(), iterations=50, verbose = false, rho = 0.95 / power_iterations(AHA), theta=1, relTol=eps(real(eltype(AHA))), restart = :none)
```

は、前方演算子 `A` または正規演算子 `AHA` のための `FISTA` オブジェクトを作成します。

# 必須引数

  * `A`                                                 - 前方演算子

または

  * `AHA`                                               - 正規演算子（キーワード引数として）

# オプションのキーワード引数

  * `AHA`                                               - `A` が供給されている場合、正規演算子はオプションです
  * `precon`                                            - 内部CGアルゴリズムのための前処理
  * `reg::AbstractParameterizedRegularization`          - 正則化項; 正則化項のベクトルでも可能
  * `normalizeReg::AbstractRegularizationNormalization` - 正則化正規化スキーム; オプションは `NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `rho::Real`                                         - 勾配ステップのためのステップサイズ; デフォルトは `0.95 / max_eigenvalue` で、パワー反復によって決定されます。
  * `theta::Real`                                       - 予測子-修正子ステップのためのパラメータ
  * `relTol::Real`                                      - 停止基準のための許容誤差
  * `iterations::Int`                                   - 最大反復回数
  * `restart::Symbol`                                   - 再起動のための `:none`, `:gradient` オプション
  * `verbose::Bool`                                     - 各反復で残差を印刷

さらに [`createLinearSolver`](@ref), [`solve!`](@ref) も参照してください。
