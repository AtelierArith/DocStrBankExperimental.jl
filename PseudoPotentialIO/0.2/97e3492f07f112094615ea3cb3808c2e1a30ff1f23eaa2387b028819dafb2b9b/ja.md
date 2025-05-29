```julia
struct NormConservingPsP{T} <: PseudoPotentialIO.NumericPsP{T}
```

数値的なノルム保存型擬ポテンシャルを表す型。

  * `checksum::Vector{UInt8}`: SHA1 チェックサム
  * `Zatom::Any`: 総電荷。
  * `Zval::Any`: バレンス電荷。
  * `lmax::Int64`: 最大角運動量。
  * `r::Union{Vector{T}, StepRangeLen{T}} where T`: 放射メッシュ。
  * `dr::Union{Vector{T}, T} where T`: 放射メッシュの間隔。
  * `Vloc::Vector`: 放射メッシュ上のポテンシャルの局所部分（r² プレファクターなし）。
  * `β::OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}} where T`: 放射メッシュ上の非局所プロジェクター β[l][n]（r² プレファクターあり）。
  * `D::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: プロジェクター結合係数 D[l][n,m]。
  * `χ::Union{Nothing, OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}}} where T`: 放射メッシュ上の擬原子波動関数 χ[l][n]（r² プレファクターあり）。
  * `ρcore::Union{Nothing, Vector{T}} where T`: 放射メッシュ上のモデルコア電荷密度（r² プレファクターあり）。
  * `ρval::Union{Nothing, Vector{T}} where T`: 放射メッシュ上のバレンス電荷密度（r² プレファクターあり）。
