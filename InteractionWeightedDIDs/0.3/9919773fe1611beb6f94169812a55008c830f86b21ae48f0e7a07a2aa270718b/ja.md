```
回帰ベースの差分の差分の推定結果。

# フィールド

  * `coef::Vector{Float64}`: 回帰係数の推定値。
  * `vcov::Matrix{Float64}`: 推定値の分散共分散行列。
  * `vce::CovarianceEstimator`: 分散共分散推定器。
  * `tr::TR`: 処置の仕様。
  * `pr::AbstractParallel`: 平行トレンドの仮定。
  * `treatweights::Vector{Float64}`: 対応する処置指標が1になる観測からの総サンプルウェイト。
  * `treatcounts::Vector{Int}`: 対応する処置指標が1になる観測の総数。
  * `esample::BitVector`: 推定に関与する`data`の行のインジケーター。
  * `nobs::Int`: 推定に関与する観測の数。
  * `dof_residual::Int`: 残差自由度。
  * `F::Float64`: 回帰モデルの全体的な有意性のためのF統計量。
  * `p::Float64`: F統計量に対応するp値。
  * `yname::String`: 結果変数の名前。
  * `coefnames::Vector{String}`: 係数の名前。
  * `coefinds::Dict{String, Int}`: 名前によって推定値を取得するための`coefnames`から整数インデックスへのマップ。
  * `treatcells::VecColumnTable`: 処置指標が1になるセルの表形式の説明。
  * `treatname::Symbol`: 処置時間を表す変数の列名。
  * `yxterms::Dict{AbstractTerm, AbstractTerm}`: 指定されたすべての項から具体的な項へのマップ。
  * `yterm::AbstractTerm`: 結果変数のために指定された項。
  * `xterms::Vector{AbstractTerm}`: 共変量と固定効果のために指定された項。
  * `contrasts::Union{Dict{Symbol, Any}, Nothing}`: `StatsModels.jl`によって処理されるコントラストコーディング。
  * `weightname::Union{Symbol, Nothing}`: サンプルウェイト変数の列名。
  * `fenames::Vector{String}`: 固定効果の名前。
  * `nfeiterations::Union{Int, Nothing}`: 固定効果ソルバーが収束に達するための反復回数。
  * `feconverged::Union{Bool, Nothing}`: 固定効果ソルバーが収束したかどうか。
  * `nfesingledropped::Int`: ドロップされた固定効果のためのシングルトン観測の数。
  * `lsweights::Union{TableIndexedMatrix, Nothing}`: セルレベルの最小二乗ウェイト。
  * `cellymeans::Union{Vector{Float64}, Nothing}`: 結果変数のセルレベルの平均。
  * `cellweights::Union{Vector{Float64}, Nothing}`: 各セルの総サンプルウェイト。
  * `cellcounts::Union{Vector{Int}, Nothing}`: 各セルの観測の数。
```
