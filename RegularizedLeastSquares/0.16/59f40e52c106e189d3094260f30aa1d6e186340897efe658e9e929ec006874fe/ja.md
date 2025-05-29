```
ADMM(A; AHA = A'*A, precon = Identity(), reg = L1Regularization(zero(real(eltype(AHA)))), regTrafo = opEye(eltype(AHA), size(AHA,1)), normalizeReg = NoNormalization(), rho = 1e-1, vary_rho = :none, iterations = 10, iterationsCG = 10, absTol = eps(real(eltype(AHA))), relTol = eps(real(eltype(AHA))), tolInner = 1e-5, verbose = false)
ADMM( ; AHA = ,     precon = Identity(), reg = L1Regularization(zero(real(eltype(AHA)))), regTrafo = opEye(eltype(AHA), size(AHA,1)), normalizeReg = NoNormalization(), rho = 1e-1, vary_rho = :none, iterations = 10, iterationsCG = 10, absTol = eps(real(eltype(AHA))), relTol = eps(real(eltype(AHA))), tolInner = 1e-5, verbose = false)
```

`ADMM`オブジェクトを前方演算子`A`または正規演算子`AHA`のために作成します。

# 必須引数

  * `A`                                                 - 前方演算子

または

  * `AHA`                                               - 正規演算子（キーワード引数として）

# オプションのキーワード引数

  * `AHA`                                               - `A`が供給されている場合、正規演算子はオプションです
  * `precon`                                            - 内部CGアルゴリズムのための前処理
  * `reg::AbstractParameterizedRegularization`          - 正則化項; 正則化項のベクトルでも可能
  * `regTrafo`                                          - `reg`が適用される空間への変換; `reg`がベクトルの場合、`regTrafo`も同じ長さのベクトルでなければなりません。変換が不要な場合は`opEye(eltype(AHA), size(AHA,1))`を使用してください。
  * `normalizeReg::AbstractRegularizationNormalization` - 正則化正規化スキーム; オプションは`NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `rho::Real`                                         - 拡張ラグランジアンのペナルティ
  * `vary_rho::Symbol`                                  - プライマルとデュアルの実現可能性をバランスさせるためにrhoを変化させる; オプション`:none`, `:balance`, `:PnP`
  * `iterations::Int`                                   - （外部）ADMM反復の最大数
  * `iterationsCG::Int`                                 - （内部）CG反復の最大数
  * `absTol::Real`                                      - 停止基準の絶対許容誤差
  * `relTol::Real`                                      - 停止基準の相対許容誤差
  * `tolInner::Real`                                    - CG停止基準の相対許容誤差
  * `verbose::Bool`                                     - 各反復で残差を印刷する

ADMMは、近接操作がペナルティが適用される空間への変換とは別に適用されるという点で、ISTA型アルゴリズムとは異なります。これは、`reg`と`regTrafo`が別々の引数としてあるインターフェースに反映されています。例えば、TVペナルティの場合、`reg=TVRegularization`を設定すべきではなく、代わりに`reg=L1Regularization(λ), regTrafo=RegularizedLeastSquares.GradientOp(Float64; shape=(Nx,Ny,Nz))`を使用してください。

さらに[`createLinearSolver`](@ref), [`solve!`](@ref)も参照してください。
