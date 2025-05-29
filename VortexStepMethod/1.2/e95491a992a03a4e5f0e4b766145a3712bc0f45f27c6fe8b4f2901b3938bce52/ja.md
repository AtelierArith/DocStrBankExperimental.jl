```
@with_kw mutable struct BodyAerodynamics{P}
```

物体の空力特性を計算するための主構造体。コンストラクタを使用して初期化します。

# フィールド

  * panels::Vector{Panel}: [Panel](@ref) 構造体のベクター
  * wings::Union{Vector{Wing}, Vector{RamAirWing}}: 複数の翼を持つことができる翼のベクター
  * `va::MVec3` = zeros(MVec3):   見かけの風速のベクター、参照: [MVec3](@ref)
  * `omega`::MVec3 = zeros(MVec3): 凧の本体軸周りの回転率のベクター
  * `gamma_distribution`=zeros(Float64, P): 速度場の循環のベクター; 長さ: セグメントの数。 [m²/s]
  * `alpha_uncorrected`=zeros(Float64, P): パネルごとの迎角
  * `alpha_corrected`=zeros(Float64, P):   パネルごとの修正された迎角
  * `stall_angle_list`=zeros(Float64, P):  パネルごとの失速角
  * `alpha_array::MVector{P, Float64}` = zeros(Float64, P)
  * `v_a_array::MVector{P, Float64}` = zeros(Float64, P)
  * `work_vectors`::NTuple{10, MVec3} = ntuple(_ -> zeros(MVec3), 10)
  * `AIC::Array{Float64, 3}` = zeros(3, P, P)
  * `projected_area::Float64` = 1.0: 凧の本体参照フレームのxy平面に投影された面積 [m²]
  * `y::MVector{P, Float64}` = zeros(MVector{P, Float64})
  * `cache::Vector{PreallocationTools.LazyBufferCache{typeof(identity), typeof(identity)}}` = [LazyBufferCache() for _ in 1:5]
