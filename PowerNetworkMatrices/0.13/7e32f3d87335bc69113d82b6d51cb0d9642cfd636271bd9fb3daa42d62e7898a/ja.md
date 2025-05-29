バーチャルライン停電分配因子（VirtualLODF）構造体は、LODF行列の行を逐次評価しながら収集します。これらの行は独立して評価され、構造体にキャッシュされ、全体の行列の計算を必要としないため（したがって計算要件を大幅に削減します）。

VirtualLODFは、保存された行がない状態で初期化されます。

VirtualLODF構造体は、ブランチ名を使用してインデックス付けされます。

# 引数

  * `K::KLU.KLUFactorization{Float64, Int}`:       KLUを用いて評価されたABA行列のLU因子分解行列。
  * `BA::SparseArrays.SparseMatrixCSC{Float64, Int}`:       BA行列。
  * `A::SparseArrays.SparseMatrixCSC{Int8, Int}`:       影響行列。
  * `inv_PTDF_A_diag::Vector{Float64}`:       PTDF行列と影響行列を掛け算した結果から得られる対角要素の要素ごとの逆数を含むベクトル。
  * `ref_bus_positions::Set{Int}`:       参照バスに対応する転置BA行列の行のインデックスを含むベクトル。
  * `axes<:NTuple{2, Dict}`:       ブランチ名を示す2つのベクトルを含むタプル。
  * `lookup<:NTuple{2, Dict}`:       ブランチ名を列挙された行インデックスにマッピングする2つの辞書を含むタプル。
  * `valid_ix::Vector{Int}`:       スラックでないバスに関連する行/列のインデックスを含むベクトル。
  * `temp_data::Vector{Float64}`:       内部使用のための一時ベクトル。
  * `cache::RowCache`:       LODF行が保存されるキャッシュ。
  * `subnetworks::Dict{Int, Set{Int}}`:       システムの異なるサブネットワークを定義するバスのサブセットを含む辞書。
  * `tol::Base.RefValue{Float64}`:       スカリフィケーションおよびドロップする値に関連する許容誤差。
  * `radial_network_reduction::RadialNetworkReduction`:       行列を評価する際に削除された放射状ブランチと葉バスを含む構造体。
