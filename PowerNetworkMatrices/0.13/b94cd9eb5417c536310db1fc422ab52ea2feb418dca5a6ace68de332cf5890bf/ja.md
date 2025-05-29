ABA行列とその他の関連データを含む構造体。

# 引数

  * `data::SparseArrays.SparseMatrixCSC{Float64, Int}`:       インシデンス行列Aと行列BAの積から得られるABA行列。
  * `axes<:NTuple{2, Dict}`:       ネットワークの各バスの番号を含む2つの同一のベクトルを含むタプル（それぞれが「data」の行/列に関連し、スラックバスを除く）。
  * `lookup<:NTuple{2, Dict}`:       行と列の番号をバスの番号にマッピングする2つの辞書を含むタプル。
  * `ref_bus_positions::Set{Int}`:       参照バスに対応するBA行列の列のインデックスを含むベクトル。
  * `K<:Union{Nothing, KLU.KLUFactorization{Float64, Int}}`:       何もないか、KLU因子分解行列（LU因子分解）のためのコンテナ。
  * `radial_network_reduction::RadialNetworkReduction`:       行列を評価する際に削除された放射状の枝と葉バスを含む構造体。
