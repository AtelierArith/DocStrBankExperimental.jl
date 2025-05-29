```
USM6{T} <: AstroCoord
```

Unified State Model Orbital Elements. 6D parameterziation of the orbit using Velocity Hodograph and MRP's C - Velocity Hodograph Component Normal to the Radial Vector Laying in the Orbital Plane Rf1 - Velocity Hodograph Component 90 degrees ahead of the Eccentricity Vector - Along the Intermediate Rotating Frame X-Axis Rf2 - Velocity Hodograph Component 90 degrees ahead of the Eccentricity Vector - Along the Intermediate Rotating Frame Y-Axis σ1 - First Modified Rodriguez Parameter  σ2 - Second Modified Rodriguez Parameter  σ3 - Third Modified Rodriguez Parameter 

Constructors USM6(C, Rf1, Rf2, σ1, σ2, σ3) USM6(X::AbstractArray) USM6(X::AstroCoord, μ::Number)
