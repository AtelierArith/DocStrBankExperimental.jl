```
UnitaryMinimumTimeProblem(
    goal::AbstractPiccoloOperator,
    trajectory::NamedTrajectory,
    objective::Objective,
    dynamics::TrajectoryDynamics,
    constraints::AbstractVector{<:AbstractConstraint};
    kwargs...
)

UnitaryMinimumTimeProblem(
    goal::AbstractPiccoloOperator,
    prob::DirectTrajOptProblem;
    kwargs...
)
```

単位制御の最小時間問題を作成します。

$$
\begin{aligned}
\underset{\vec{\tilde{U}}, a, \dot{a}, \ddot{a}, \Delta t}{\text{minimize}} & \quad
J(\vec{\tilde{U}}, a, \dot{a}, \ddot{a}) + D \sum_t \Delta t_t \\
\text{ subject to } & \quad \vb{P}^{(n)}\qty(\vec{\tilde{U}}_{t+1}, \vec{\tilde{U}}_t, a_t, \Delta t_t) = 0 \\
& c(\vec{\tilde{U}}, a, \dot{a}, \ddot{a}) = 0 \\
& \quad \Delta t_{\text{min}} \leq \Delta t_t \leq \Delta t_{\text{max}} \\
\end{aligned}
$$

# キーワード引数

  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: Piccoloのオプション。
  * `unitary_name::Symbol=:Ũ⃗`: 目標の単位の名前。
  * `final_fidelity::Float64=1.0`: 最終的な忠実度制約。
  * `D::Float64=1.0`: 最小時間目的のスケーリングファクター。
