```
struct PointMassSystem
```

A discrete mass-spring-damper representation of a kite system, where point masses  connected by elastic segments model the kite and tether dynamics:

  * `points::Vector{Point}`: Point masses representing:

      * Kite attachment points
      * Dynamic bridle/tether points
      * Fixed ground anchor points
  * `groups::Vector{KitePointGroup}`: Collections of points that move together,    according to kite deformation (twist and trailing edge deflection)
  * `segments::Vector{Segment}`: Spring-damper elements between points
  * `pulleys::Vector{Pulley}`: Elements that redistribute line lengths
  * `tethers::Vector{Tether}`: Groups of segments with a common unstretched length
  * `winches::Vector{Winch}`: Ground-based winches that control the tether lengths

See also: [`Point`](@ref), [`Segment`](@ref), [`KitePointGroup`](@ref), [`Pulley`](@ref)
