```
SplitBregman(A; AHA = A'*A, precon = Identity(), reg = L1Regularization(zero(real(eltype(AHA)))), regTrafo = opEye(eltype(AHA), size(AHA,1)), normalizeReg = NoNormalization(), rho = 1e-1, iterations = 10, iterationsInner = 10, iterationsCG = 10, absTol = eps(real(eltype(AHA))), relTol = eps(real(eltype(AHA))), tolInner = 1e-5, verbose = false)
SplitBregman( ; AHA = ,     precon = Identity(), reg = L1Regularization(zero(real(eltype(AHA)))), regTrafo = opEye(eltype(AHA), size(AHA,1)), normalizeReg = NoNormalization(), rho = 1e-1, iterations = 10, iterationsInner = 10, iterationsCG = 10, absTol = eps(real(eltype(AHA))), relTol = eps(real(eltype(AHA))), tolInner = 1e-5, verbose = false)
```

`SplitBregman`オブジェクトを前方演算子`A`または正規演算子`AHA`のために作成します。

# 必要な引数

  * `A`                                                 - 前方演算子

または

  * `AHA`                                               - 正規演算子（キーワード引数として）

# オプションのキーワード引数

  * `AHA`                                               - `A`が供給されている場合、正規演算子はオプションです
  * `precon`                                            - 内部CGアルゴリズムのための前処理
  * `reg::AbstractParameterizedRegularization`          - 正則化項；正則化項のベクトルでも可能
  * `regTrafo`                                          - `reg`が適用される空間への変換；`reg`がベクトルの場合、`regTrafo`も同じ長さのベクトルでなければなりません。変換が不要な場合は`opEye(eltype(AHA), size(AHA,1))`を使用してください。
  * `normalizeReg::AbstractRegularizationNormalization` - 正則化正規化スキーム；オプションは`NoNormalization()`, `MeasurementBasedNormalization()`, `SystemMatrixBasedNormalization()`
  * `rho::Real`                                         - 正則化された変数に対する条件の重み；複数の正則化項のためのベクトルでも可能
  * `iterations::Int`                              - 外部反復の最大数。制約のないスプリットBregmanのために1に設定（ADMMに相当）
  * `iterationsInner::Int`                              - 内部反復の最大数
  * `iterationsCG::Int`                                 - （内部）CG反復の最大数
  * `absTol::Real`                                      - 停止基準の絶対許容誤差
  * `relTol::Real`                                      - 停止基準の相対許容誤差
  * `tolInner::Real`                                    - CG停止基準の相対許容誤差
  * `verbose::Bool`                                     - 各反復で残差を印刷

このアルゴリズムは制約問題（[Tom Goldstein and Stanley Osher](https://doi.org/10.1137/080725891)の式(4.7)）を解決します。すなわち、`||R(x)||₁`が`||Ax -b||₂² < σ²`となるようにします。制約のない問題（[Tom Goldstein and Stanley Osher](https://doi.org/10.1137/080725891)の式(4.8)）を解決するには、`iterations=1`を設定するか、ADMMを使用することができます。これは同等です（SplitBregmanの`iterations=1`はADMMに暗黙的に含まれ、SplitBregman変数`iterationsInner`はADMMでは単に`iterations`と呼ばれます）。

ADMMと同様に、SplitBregmanはISTA型アルゴリズムとは異なり、近接操作がペナルティが適用される空間への変換とは別に適用されます。これは、`reg`と`regTrafo`が別々の引数としてあるインターフェースに反映されています。例えば、TVペナルティの場合、`reg=TVRegularization`を設定すべきではなく、代わりに`reg=L1Regularization(λ), regTrafo=RegularizedLeastSquares.GradientOp(Float64; shape=(Nx,Ny,Nz))`を使用してください。

[`createLinearSolver`](@ref)や[`solve!`](@ref)も参照してください。
