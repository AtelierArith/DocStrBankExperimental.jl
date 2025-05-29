構造体はMRI取得データを記述します。

# フィールド

  * `sequenceInfo::Dict{Symbol,Any}`          - パルスシーケンスに関する追加情報
  * `traj::Vector{Trajectory}`                - 各エコー/コントラストのための軌道
  * `kdata::Array{Matrix{Complex{<:AbstractFloat}},3}`      - 各行列は1つの軌道のデータを含みます                                             (1. 次元 k空間ノード, 2. 次元 コイル)                                             外側の次元は次のように説明されます:                                             1. 次元 エコー, 2. 次元 スライス, 3. 次元 繰り返し
  * `subsampleIndices::Vector{Array{Int64}}`  - 各エコー/コントラストのためにサンプリングされたインデックス
  * `encodingSize::Vector{Int64}`             - 基本となる画像行列のサイズ
  * `fov::Vector{Float64}`                    - 視野の大きさ（mm単位）
