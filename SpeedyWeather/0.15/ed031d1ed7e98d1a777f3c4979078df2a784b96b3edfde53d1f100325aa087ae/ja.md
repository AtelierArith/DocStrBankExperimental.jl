温度緩和（Held and Suarez, 1996 BAMS）

  * `nlat::Int64`: 緯度リングの数
  * `nlayers::Int64`: 垂直レベルの数
  * `σb::AbstractFloat`: より速い表面緩和が適用されるシグマ座標
  * `relax_time_slow::Dates.Second`: ゆっくりした全球緩和の時間スケール
  * `relax_time_fast::Dates.Second`: より速い熱帯表面緩和の時間スケール
  * `Tmin::AbstractFloat`: 最小平衡温度 [K]
  * `Tmax::AbstractFloat`: 最大平衡温度 [K]
  * `ΔTy::AbstractFloat`: 経度方向の温度勾配 [K]
  * `Δθz::AbstractFloat`: 垂直方向の温度勾配 [K]
  * `κ::Base.RefValue{NF} where NF<:AbstractFloat`
  * `p₀::Base.RefValue{NF} where NF<:AbstractFloat`
  * `temp_relax_freq::Matrix{NF} where NF<:AbstractFloat`
  * `temp_equil_a::Vector{NF} where NF<:AbstractFloat`
  * `temp_equil_b::Vector{NF} where NF<:AbstractFloat`
