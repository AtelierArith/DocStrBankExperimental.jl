```
POGM(A; AHA = A'*A, reg = L1Regularization(zero(real(eltype(AHA)))), normalizeReg = NoNormalization(), iterations = 50, verbose = false, rho = 0.95 / power_iterations(AHA), theta = 1, sigma_fac = 1, relTol = eps(real(eltype(AHA))), restart = :none)
POGM( ; AHA = ,     reg = L1Regularization(zero(real(eltype(AHA)))), normalizeReg = NoNormalization(), iterations = 50, verbose = false, rho = 0.95 / power_iterations(AHA), theta = 1, sigma_fac = 1, relTol = eps(real(eltype(AHA))), restart = :none)
```

`POGM`オブジェクトを前方演算子`A`または正規演算子`AHA`のために作成します。POGMはFISTAよりも最悪の場合の境界が2倍良いですが、実際のパフォーマンスはアプリケーションによって異なります。FISTAと比較して、画像のサイズと同じ3つの追加の中間変数を保存します。現在のところ、勾配再起動スキームのみが実装されています。

# 参考文献:

  * A.B. Taylor, J.M. Hendrickx, F. Glineur,   "合成凸最適化のための一次アルゴリズムの正確な最悪ケース性能," Arxiv:1512.07516, 2015,   SIAM J. Opt. 2017   [http://doi.org/10.1137/16m108104x]
  * Kim, D., & Fessler, J. A. (2018).   凸最適化のための最適化勾配法の適応再起動.   最適化理論と応用のジャーナル, 178(1), 240–263.   [https://doi.org/10.1007/s10957-018-1287-4]

    # 必要な引数

      * `A`                                                 - 前方演算子

    または

      * `AHA`                                               - 正規演算子（キーワード引数として）

    # オプションのキーワード引数

      * `AHA`                                               - `A`が供給されている場合、正規演算子はオプション
      * `reg::AbstractParameterizedRegularization`          - 正則化項
      * `normalizeReg::AbstractRegularizationNormalization` - 正則化正規化スキーム; オプションは`NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
      * `rho::Real`                                         - 勾配ステップのステップサイズ; デフォルトは`0.95 / max_eigenvalue`で、パワー反復によって決定されます。
      * `theta::Real`                                       - 予測子-修正ステップのパラメータ
      * `sigma_fac::Real`                                   - 減少するγ-モメンタムのパラメータ ∈ [0,1]
      * `relTol::Real`                                      - 停止基準の許容誤差
      * `iterations::Int`                                   - 最大反復回数
      * `restart::Symbol`                                   - 再起動のための`:none`, `:gradient`オプション
      * `verbose::Bool`                                     - 各反復で残差を印刷

[`createLinearSolver`](@ref)や[`solve!`](@ref)も参照してください。
