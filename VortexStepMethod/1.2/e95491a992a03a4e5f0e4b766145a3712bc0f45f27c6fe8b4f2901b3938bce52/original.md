```
@with_kw mutable struct BodyAerodynamics{P}
```

Main structure for calculating aerodynamic properties of bodies. Use the constructor to initialize.

# Fields

  * panels::Vector{Panel}: Vector of [Panel](@ref) structs
  * wings::Union{Vector{Wing}, Vector{RamAirWing}}: A vector of wings; a body can have multiple wings
  * `va::MVec3` = zeros(MVec3):   A vector of the apparent wind speed, see: [MVec3](@ref)
  * `omega`::MVec3 = zeros(MVec3): A vector of the turn rates around the kite body axes
  * `gamma_distribution`=zeros(Float64, P): A vector of the circulation                        of the velocity field; Length: Number of segments. [m²/s]
  * `alpha_uncorrected`=zeros(Float64, P): angles of attack per panel
  * `alpha_corrected`=zeros(Float64, P):   corrected angles of attack per panel
  * `stall_angle_list`=zeros(Float64, P):  stall angle per panel
  * `alpha_array::MVector{P, Float64}` = zeros(Float64, P)
  * `v_a_array::MVector{P, Float64}` = zeros(Float64, P)
  * `work_vectors`::NTuple{10, MVec3} = ntuple(_ -> zeros(MVec3), 10)
  * `AIC::Array{Float64, 3}` = zeros(3, P, P)
  * `projected_area::Float64` = 1.0: The area projected onto the xy-plane of the kite body reference frame [m²]
  * `y::MVector{P, Float64}` = zeros(MVector{P, Float64})
  * `cache::Vector{PreallocationTools.LazyBufferCache{typeof(identity), typeof(identity)}}` = [LazyBufferCache() for _ in 1:5]
