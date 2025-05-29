可変構造体は、表面速度データを表します。すべてのフィールドは、デフォルト値として `nothing` を提供することで空にすることができます。

`SurfaceVelocityData{F <: AbstractFloat} <: AbstractData`

# フィールド

  * `x::Union{Vector{F}, Nothing}`: 観測の東方向。
  * `y::Union{Vector{F}, Nothing}`: 観測の北方向。
  * `lat::Union{Vector{F}, Nothing}`: 観測の緯度。
  * `lon::Union{Vector{F}, Nothing}`: 観測の経度。
  * `vx::Union{Vector{Matrix{F}}, Nothing}`: 表面速度のx成分。
  * `vy::Union{Vector{Matrix{F}}, Nothing}`: 表面速度のy成分。
  * `vabs::Union{Vector{Matrix{F}}, Nothing}`: 絶対氷表面速度。
  * `vx_error::Union{Vector{F}, Nothing}`: `vx` の誤差。
  * `vy_error::Union{Vector{F}, Nothing}`: `vy` の誤差。
  * `vabs_error::Union{Vector{F}, Nothing}`: `vabs` の誤差。
  * `date::Union{Vector{DateTime}, Nothing}`: 観測の日付（`date1` と `date2` の平均）
  * `date1::Union{Vector{DateTime}, Nothing}`: 取得の最初の日付。
  * `date2::Union{Vector{DateTime}, Nothing}`: 取得の2番目の日付。
  * `date_error::Union{Vector{Day}, Vector{Millisecond}, Nothing}`: `date` の誤差。
  * `isGridGlacierAligned::Bool`: データが氷河グリッドにグリッド化されているかどうか。
