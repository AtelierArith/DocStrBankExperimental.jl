```julia
struct Psp8File <: PseudoPotentialIO.PsPFile
```

ABINIT PSeudoPotential format 8ファイルの内容。ファイル形式の仕様とファイル内の量の意味については、ABINITドキュメントの["psp8"ページ](https://docs.abinit.org/developers/psp8_info/)を参照してください。

  * `checksum::Vector{UInt8}`: SHA1チェックサム
  * `header::PseudoPotentialIO.Psp8Header`: 様々な擬似ポテンシャルメタデータ
  * `rgrid::Vector{Float64}`: `r = 0.0`から始まる均一な半径グリッド
  * `v_local::Vector{Float64}`: 擬似ポテンシャルの局所部分
  * `projectors::Vector{Vector{Vector{Float64}}}`: 各角運動量に対するクラインマン-バイランダー射影器の半径部分
  * `ekb::Vector{Vector{Float64}}`: 各角運動量に対するクラインマン-バイランダーエネルギー
  * `projectors_so::Union{Nothing, Vector{Vector{Vector{Float64}}}}`: 各角運動量に対するスピン-軌道クラインマン-バイランダー射影器の半径部分
  * `ekb_so::Union{Nothing, Vector{Vector{Float64}}}`: 各角運動量に対するスピン-軌道クラインマン-バイランダーエネルギー
  * `rhoc::Union{Nothing, Vector{Float64}}`: モデルコア電荷密度
  * `d_rhoc_dr::Union{Nothing, Vector{Float64}}`: モデルコア電荷密度の一次導関数
  * `d2_rhoc_dr2::Union{Nothing, Vector{Float64}}`: モデルコア電荷密度の二次導関数
  * `d3_rhoc_dr3::Union{Nothing, Vector{Float64}}`: モデルコア電荷密度の三次導関数
  * `d4_rhoc_dr4::Union{Nothing, Vector{Float64}}`: モデルコア電荷密度の四次導関数
