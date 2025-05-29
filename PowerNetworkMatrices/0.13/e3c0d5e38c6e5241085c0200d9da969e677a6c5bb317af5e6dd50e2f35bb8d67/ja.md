BA行列とその他の関連データを含む構造体。

# 引数

  * `data::SparseArrays.SparseMatrixCSC{Float64, Int}`:       伝送行列Aと感受性行列Bの積から得られる転置BA行列
  * `axes<:NTuple{2, Dict}`:       2つのベクトルを含むタプル。最初のベクトルはネットワークの各バスの名前を含み（それぞれが「data」の行に関連）、2番目のベクトルはネットワークの各ラインの名前を含む（それぞれが「data」の列に関連）
  * `lookup<:NTuple{2, Dict}`:       バスとブランチの名前に対応する行と列の数をマッピングする2つの辞書を含むタプル
  * `ref_bus_positions::Set{Int}`:       参照バスに対応するBA行列の列のインデックスを含むセット
  * `radial_network_reduction::RadialNetworkReduction`:       行列を評価する際に削除された放射状ブランチと葉バスを含む構造体
