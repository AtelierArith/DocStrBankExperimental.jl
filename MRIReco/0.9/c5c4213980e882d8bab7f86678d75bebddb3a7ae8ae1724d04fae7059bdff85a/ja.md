すべてのコイル、コントラスト、およびスライスのデータに対して独立に反復画像再構成を実行します。

# 引数

  * `acqData::AcquisitionData`            - AcquisitionDataオブジェクト
  * `reconSize::NTuple{2,Int64}`              - 再構成する画像のサイズ
  * `reg::Vector{<:AbstractRegularization}`                 - 使用する正則化
  * `sparseTrafo::AbstractLinearOperator` - スパース化変換
  * `weights::Vector{Vector{Complex{<:AbstractFloat}}}` - acqData内の軌道のサンプリング密度
  * `solver::Type{<:AbstractLinearSolver}`                  - 使用するソルバーの名前
  * (`normalize::Bool=false`)             - k空間データのサイズに応じて正則化パラメータを調整
  * (`params::Dict{Symbol,Any}`)          - 追加のパラメータを含むDict
