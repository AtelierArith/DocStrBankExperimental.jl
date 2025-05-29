A mutable struct representing the excution configuration of a FMU. For FMUs that have issues with calls like `fmi2Reset` or `fmi2FreeInstance`, this is pretty useful.

# Fields

  * `terminate::Bool`: Call `fmi2Terminate` before every training step/simulation.
  * `reset::Bool`: Call `fmi2Reset` before every training step/simulation.
  * `setup::Bool`: Call setup functions before every training step/simulation.
  * `instantiate::Bool`: Call `fmi2Instantiate` before every training step/simulation.
  * `freeInstance::Bool`: Call `fmi2FreeInstance` after every training step/simulation.
  * `loggingOn::Bool`: Enable or disable logging.
  * `externalCallbacks::Bool`: Use external callbacks.
  * `force::Bool`: Default value for forced actions.
  * `handleStateEvents::Bool`: Handle state events during simulation/training.
  * `handleTimeEvents::Bool`: Handle time events during simulation/training.
  * `assertOnError::Bool`: Whether an exception is thrown if a `fmi2XXX` command fails (>= `fmi2StatusError`).
  * `assertOnWarning::Bool`: Whether an exception is thrown if a `fmi2XXX` command warns (>= `fmi2StatusWarning`).
  * `autoTimeShift::Bool`: Whether to shift all time-related functions for simulation intervals not starting at 0.0.
  * `inplace_eval::Bool`: Whether FMU/Component evaluation should happen in place.
  * `sensealg::Any`: Algorithm for sensitivity estimation over solve call ([ToDo] Datatype/Nothing).
  * `rootSearchInterpolationPoints::UInt`: Number of root search interpolation points.
  * `useVectorCallbacks::Bool`: Whether to use vector (faster) or scalar (slower) callbacks.
  * `maxNewDiscreteStateCalls::UInt`: Max calls for `fmi2NewDiscreteStates` before throwing an exception.
  * `maxStateEventsPerSecond::UInt`: Max state events allowed to occur per second (more is interpreted as event chattering).
  * `snapshotDeltaTimeTolerance::Float64`: Distance to distinguish between snapshots.
  * `eval_t_gradients::Bool`: If time gradients ∂ẋ/∂t and ∂y/∂t should be sampled (not part of the FMI standard).
  * `JVPBuiltInDerivatives::Bool`: Use built-in directional derivatives for JVP-sensitivities over FMU without caching the Jacobian (because this is done in the FMU, but not per default).
  * `VJPBuiltInDerivatives::Bool`: Use built-in adjoint derivatives for VJP-sensitivities over FMU without caching the Jacobian (because this is done in the FMU, but not per default).
  * `sensitivity_strategy::Symbol`: Build-up strategy for Jacobians/gradients, available options are `:FMIDirectionalDerivative`, `:FMIAdjointDerivative`, `:FiniteDiff`.
  * `set_p_every_step::Bool`: Whether parameters are set for every simulation step - this is uncommon, because parameters are often set just one time: during/after initialization.
  * `concat_eval::Bool`: (Deprecated) Whether FMU/Component evaluation should return a tuple `(y, dx, ec)` or a concatenation `[y..., dx..., ec...]`.
