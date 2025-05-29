```julia
struct TrustRegionSolver{L, O, U<:(AbstractVector), W, T<:TimerOutputs.TimerOutput, F<:FiniteElementContainers.NodalField, S<:Cthonios.TrustRegionSolverSettings} <: Cthonios.AbstractNonlinearSolver{L, O, U<:(AbstractVector), W, T<:TimerOutputs.TimerOutput}
```

  * `preconditioner::Any`
  * `objective::Any`
  * `ΔUu::AbstractVector`
  * `warm_start::Any`
  * `timer::TimerOutputs.TimerOutput`
  * `o::AbstractVector`
  * `g::FiniteElementContainers.NodalField`
  * `Hv::FiniteElementContainers.NodalField`
  * `cauchy_point::AbstractVector`
  * `q_newton_point::AbstractVector`
  * `d::AbstractVector`
  * `y_scratch_1::AbstractVector`
  * `y_scratch_2::AbstractVector`
  * `y_scratch_3::AbstractVector`
  * `y_scratch_4::AbstractVector`
  * `use_warm_start::Bool`
  * `settings::Cthonios.TrustRegionSolverSettings`
