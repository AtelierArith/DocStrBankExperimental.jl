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

Create a minimum-time problem for unitary control.

$$
\begin{aligned}
\underset{\vec{\tilde{U}}, a, \dot{a}, \ddot{a}, \Delta t}{\text{minimize}} & \quad
J(\vec{\tilde{U}}, a, \dot{a}, \ddot{a}) + D \sum_t \Delta t_t \\
\text{ subject to } & \quad \vb{P}^{(n)}\qty(\vec{\tilde{U}}_{t+1}, \vec{\tilde{U}}_t, a_t, \Delta t_t) = 0 \\
& c(\vec{\tilde{U}}, a, \dot{a}, \ddot{a}) = 0 \\
& \quad \Delta t_{\text{min}} \leq \Delta t_t \leq \Delta t_{\text{max}} \\
\end{aligned}
$$

# Keyword Arguments

  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: The Piccolo options.
  * `unitary_name::Symbol=:Ũ⃗`: The name of the unitary for the goal.
  * `final_fidelity::Float64=1.0`: The final fidelity constraint.
  * `D::Float64=1.0`: The scaling factor for the minimum-time objective.
