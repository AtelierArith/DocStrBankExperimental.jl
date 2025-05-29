軌道を記述する構造体

# フィールド

  * `name::String`                  - 軌道の名前
  * `nodes::Matrix{Float64}`        - k空間におけるサンプリング位置。                                   (1次元 <-> k空間の次元、2次元 <-> サンプリングポイント)
  * `times::Vector{Float64}`        - サンプリング時間（秒）
  * `TE::Float64`                   - エコー時間（秒）
  * `AQ::Float64``                  - 読出し時間（秒）（プロファイルごと）
  * `numProfiles::Int64`            - プロファイルの数
  * `numSamplingPerProfile::Int64`  - プロファイルごとのサンプリングポイントの数
  * `numSlices::Int64`              - スライスの数（3D軌道用）
  * `cartesian::Bool`               - サンプリングポイントが直交格子上にある場合はtrue
  * `circular::Bool`                - k空間が円形領域でカバーされている場合はtrue
