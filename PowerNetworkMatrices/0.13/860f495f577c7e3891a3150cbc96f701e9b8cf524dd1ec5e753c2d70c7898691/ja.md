インシデンス行列: バス間の接続を示し、ラインを定義します

# 引数

  * `data::SparseArrays.SparseMatrixCSC{Int8, Int}`:       実際のインシデンス行列。
  * `axes<:NTuple{2, Dict}`:       2つのベクトルを含むタプル（最初のベクトルはブランチ名を示し、       2番目のベクトルはバス番号を示します）。
  * `lookup<:NTuple{2, Dict}`:       2つの辞書を含むタプルで、最初の辞書はブランチとバスを       列挙されたインデックスにマッピングします。
  * `ref_bus_positions::Set{Int}`:       参照スラックバスのインデックスを含むベクター。
  * `radial_network_reduction::RadialNetworkReduction`:       行列を評価する際に削除された放射状ブランチとリーフバスを含む構造体。
