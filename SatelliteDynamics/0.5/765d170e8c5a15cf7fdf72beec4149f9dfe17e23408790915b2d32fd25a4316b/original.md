Simulate the sttate dynamics to the specified time. Takes same inputs as `stepto!` but instead of just updating the state vector to the specified time, this  function also returns the timesteps, state values, and state transition matrices for each time step.

Arguments:

  * `state::EarthInertialState` State vector to propagate
  * `time::Union{Real, Epoch}` Time to propagate internal state too. Can be either

a real number to advance the state by or the Epoch

Returns:

  * `t::AbstractArray{Float64, 1}` Elapsed time as a scalar from the initial simulation epoch
  * `epc::AbstractArray{Epoch, 1}` Epoch at each timestep
  * `x::AbstractArray{Float64, 2}` State vectors at each time step. Time is along second axis
  * `Phi::AbstractArray{Float64, 2}` Stacked array of state transition matrices
