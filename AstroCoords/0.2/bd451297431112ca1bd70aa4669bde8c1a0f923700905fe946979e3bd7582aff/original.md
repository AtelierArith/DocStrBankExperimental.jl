```
USMEM{T} <: AstroCoord
```

Unified State Model Orbital Elements. 6D parameterziation of the orbit using Velocity Hodograph and Exponential Mapping C - Velocity Hodograph Component Normal to the Radial Vector Laying in the Orbital Plane Rf1 - Velocity Hodograph Component 90 degrees ahead of the Eccentricity Vector - Along the Intermediate Rotating Frame X-Axis Rf2 - Velocity Hodograph Component 90 degrees ahead of the Eccentricity Vector - Along the Intermediate Rotating Frame Y-Axis a1 - First Exponential Mapping Component a2 - Second Exponential Mapping Component a3 - Third Exponential Mapping Component

Constructors USMEM(C, Rf1, Rf2, a1, a2, a3) USMEM(X::AbstractArray) USMEM(X::AstroCoord, μ::Number)
