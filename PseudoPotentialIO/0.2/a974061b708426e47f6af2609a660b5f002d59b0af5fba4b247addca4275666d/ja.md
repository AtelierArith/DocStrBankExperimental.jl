```julia
struct HghFile <: PseudoPotentialIO.PsPFile
```

Hartwigsen-Goedecker-Hutter擬ポテンシャルファイルの内容。

  * `checksum::Vector{UInt8}`: SHA1チェックサム
  * `title::String`: 説明
  * `zion::Vector{Int64}`: 擬原子（価電子）電荷
  * `rloc::Float64`: 擬ポテンシャルの局所部分のカットオフ半径
  * `nloc::Int64`: 擬ポテンシャルの局所部分を定義する係数の数
  * `cloc::Vector{Float64}`: 擬ポテンシャルの局所部分の係数
  * `lmax::Int64`: 最大角運動量
  * `rp::Vector{Float64}`: 各角運動量の非局所プロジェクタのカットオフ半径
  * `h::Vector{Matrix{Float64}}`: クラインマン-バイランダーエネルギー
