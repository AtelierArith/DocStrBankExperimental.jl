`MatrixCorrection` is an abstract type for computing ϕ(ρz)-type matrix correction algorithms.  A sub-class `MCA <: MatrixCorrection` should implement

```
# Integral of the area under the ϕ(ρz)-curve
ℱ(mc::MCA)
# Integral of the transmitted area under the ϕ(ρz)-curve
ℱχ(mc::MCA, xray::CharXRay, θtoa::AbstractFloat)
# Area under 0 to τ under the transmitted ϕ(ρz)-curve
ℱχp(mc::MCA, xray::CharXRay, θtoa::AbstractFloat, τ::AbstractFloat)
# The ϕ(ρz)-curve
ϕ(mc::MCA, ρz)
# A factory method from MCA
matrixcorrection(::Type{MCA}, mat::Material, ashell::AtomicSubShell, e0)::MCA
```

The algorithm should precompute as much as possible based on the `Material`, `AtomicSubShell` and beam energy.  The class `MCA` should define member variables `subshell::AtomicSubShell`, `material::Material` and `E0::AbstractFloat` to store the input values. See `XPP` for an example.

From these methods, other methods like `Z(...)`, `A(...)` are implemented.
