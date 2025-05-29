```julia
struct Pose2Pose2{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Rigid transform between two Pose2's, assuming (x,y,theta).

Calcuated as:

$$
\begin{aligned}
\hat{q}=\exp_pX_m\\
X = \log_q \hat{q}\\
X^i = \mathrm{vee}(q, X)
\end{aligned}
$$

with: $\mathcal M= \mathrm{SE}(2)$ Special Euclidean group
$p$ and $q$ $\in \mathcal M$ the two Pose2 points
the measurement vector $X_m \in T_p \mathcal M$
and the error vector $X \in T_q \mathcal M$
$X^i$ coordinates of $X$

DevNotes

  * Maybe with Manifolds.jl, `{T <: IIF.SamplableBelief, S, R, P}`

Related

[`Pose3Pose3`](@ref), [`Point2Point2`](@ref), [`MutablePose2Pose2Gaussian`](@ref), [`DynPose2`](@ref), [`IMUDeltaFactor`](@ref)
