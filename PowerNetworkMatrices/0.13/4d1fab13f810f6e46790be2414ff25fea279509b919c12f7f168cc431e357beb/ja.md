The Virtual Power Transfer Distribution Factor (VirtualPTDF) 構造体は、PTDF 行列の行を逐次評価しながら収集します。これらの行は独立して評価され、構造体にキャッシュされ、全体の行列の計算を必要としないため（したがって計算要件が大幅に削減されます）。

VirtualPTDF は、保存された行がない状態で初期化されます。

VirtualPTDF は、PTDF 行列と同様に、ブランチ名とバス番号を使用してインデックス付けされます。

# 引数

  * `K::KLU.KLUFactorization{Float64, Int}`:       KLU によって評価された ABA 行列の LU 因子分解行列
  * `BA::SparseArrays.SparseMatrixCSC{Float64, Int}`:       BA 行列
  * `ref_bus_positions::Set{Int}`:       参照バスに対応する BA 行列の列のインデックスを含むベクター
  * `dist_slack::Vector{Float64}`:       分散スラックバスとして使用される重みのベクター。       分散スラックベクターは、バスの数と同じ長さでなければなりません。
  * `axes<:NTuple{2, Dict}`:       2 つのベクターを含むタプル：最初のベクターはブランチ名を示し、       2 番目のベクターはバス番号を示します。ブランチ名のベクターの順序と       PTDF 行がキャッシュに保存される方法との間に関連はありません。
  * `lookup<:NTuple{2, Dict}`:       ブランチとバスを列挙されたインデックスにマッピングする 2 つの辞書を含むタプル。ブランチインデックスは       キャッシュ辞書のキーを参照します。バスインデックスは、保存された PTDF 行の要素の位置を参照します。
  * `temp_data::Vector{Float64}`:       内部使用のための一時ベクター。
  * `valid_ix::Vector{Int}`:       スラックでないバスに関連する行/列のインデックスを含むベクター。
  * `cache::RowCache`:       PTDF 行が保存されるキャッシュ。
  * `subnetworks::Dict{Int, Set{Int}}`:       システムの異なるサブネットワークを定義するバスのサブセットを含む辞書。
  * `tol::Base.RefValue{Float64}`:       スカリフィケーションおよびドロップする値に関連する許容誤差。
  * `radial_network_reduction::RadialNetworkReduction`:       行列を評価する際に削除された放射状ブランチと葉バスを含む構造体。
