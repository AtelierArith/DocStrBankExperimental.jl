```julia
struct UltrasoftPsP{T} <: PseudoPotentialIO.NumericPsP{T}
```

数値ウルトラソフト擬ポテンシャルを表す型。

  * `Zatom::Any`: 総電荷
  * `Zval::Any`: バレンス電荷
  * `lmax::Int64`: 最大角運動量
  * `r::Vector`: 放射メッシュ
  * `dr::Union{Vector{T}, T} where T`: 放射メッシュ間隔
  * `Vloc::Vector`: 放射メッシュ上のポテンシャルの局所部分
  * `β::OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}} where T`: 放射メッシュ上の非局所プロジェクタ β[l][n]
  * `D::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: プロジェクタ結合係数 D[l][n,m]
  * `χ::OffsetArrays.OffsetArray{Array{Vector{T}, 1}, 1, Array{Array{Vector{T}, 1}, 1}} where T`: 放射メッシュ上の擬原子波動関数 χ[l][n]
  * `Q::OffsetArrays.OffsetArray{Array{Vector{T}, 2}, 1, Array{Array{Vector{T}, 2}, 1}} where T`: 放射メッシュ上の増強電荷密度関数 Q[l][n,m]
  * `q::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: 増強電荷 q[l][n,m]
  * `ρcore::Union{Nothing, Vector{T}} where T`: 放射メッシュ上の非線形コア補正のためのモデルコア電荷密度
  * `ρval::Union{Nothing, Vector{T}} where T`: 放射メッシュ上の電荷密度初期化のためのバレンス電荷密度
