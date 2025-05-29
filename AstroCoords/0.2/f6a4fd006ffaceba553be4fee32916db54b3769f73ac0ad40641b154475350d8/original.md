```
USM7{T} <: AstroCoord
```

Unified State Model Orbital Elements. 7D parameterziation of the orbit using Velocity Hodograph and Quaternions C - Velocity Hodograph Component Normal to the Radial Vector Laying in the Orbital Plane Rf1 - Velocity Hodograph Component 90 degrees ahead of the Eccentricity Vector - Along the Intermediate Rotating Frame X-Axis Rf2 - Velocity Hodograph Component 90 degrees ahead of the Eccentricity Vector - Along the Intermediate Rotating Frame Y-Axis ϵO1 - First Imaginary Quaternion Component ϵO2 - Second Imaginary Quaternion Component ϵO3 - Third Imaginary Quaternion Component η0 - Real Quaternion Component

Constructors USM7(C, Rf1, Rf2, ϵO1, ϵO2, ϵO3, η0) USM7(X::AbstractArray) USM7(X::AstroCoord, μ::Number)
