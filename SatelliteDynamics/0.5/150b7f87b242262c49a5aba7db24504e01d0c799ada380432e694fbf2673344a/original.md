Performs single integration step of numerical integrator.

Arguments:

  * `rk4::RK4` 4-th order Runge-Kutta numerical integrator object
  * `epc::Union{Real, Epoch}` Absolute time of start of integration step
  * `dt::Real` Integration step size
  * `x::AbstractArray{<:Real, 1}` State vector
  * `phi::AbstractArray{<:Real, 2}` State transition matrix at start of integration step
