```julia
struct Pose2Pose2{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

二つのPose2間の剛体変換、(x,y,theta)を仮定します。

次のように計算されます：

$$
\begin{aligned}
\hat{q}=\exp_pX_m\\
X = \log_q \hat{q}\\
X^i = \mathrm{vee}(q, X)
\end{aligned}
$$

ここで：$\mathcal M= \mathrm{SE}(2)$ 特殊ユークリッド群 $p$と$q$は$\mathcal M$に属する二つのPose2点 測定ベクトル$X_m \in T_p \mathcal M$ および誤差ベクトル$X \in T_q \mathcal M$ $X^i$は$X$の座標です

DevNotes

  * おそらくManifolds.jlを使用して、`{T <: IIF.SamplableBelief, S, R, P}`

関連

[`Pose3Pose3`](@ref), [`Point2Point2`](@ref), [`MutablePose2Pose2Gaussian`](@ref), [`DynPose2`](@ref), [`IMUDeltaFactor`](@ref)
