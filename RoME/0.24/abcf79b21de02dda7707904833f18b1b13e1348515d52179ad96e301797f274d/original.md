```julia
struct Pose3Pose3XYYaw{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Partial factor between XY and Yaw of two Pose3 variables.

```
wR2 = wR1*1R2 = wR1*(1Rψ*Rθ*Rϕ)
wRz = wR1*1Rz
zRz = wRz \ wR(Δψ)

M_R = SO(3)
δ(α,β,γ) = vee(M_R, R_0, log(M_R, R_0, zRz))

M = SE(3)
p0 = identity_element(M)
δ(x,y,z,α,β,γ) = vee(M, p0, log(M, p0, zRz))
```
