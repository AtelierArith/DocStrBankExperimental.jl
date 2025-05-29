```
CartesianTrajectory2D{T,I,U,V} <: CartesianTrajectory{T}
```

Struct that is used to implement a typical Cartesian 2D gradient trajectory. The trajectory is described in a compact fashion by only storing the starting position in k-space (`k_start_readout`) for each readout as well as the step in k-space per readout point `Δk_adc`.

Note that CartesianTrajectory2D and RadialTrajectory2D are essentially the same when using this compact description. A SpokesTrajectory struct is therefore defined as a supertype of both and methods are defined for SpokesTrajectory instead to avoid code repetition.

The type parameters are intentionally left vague. The `J`, for example, may be an integer for sequences where each readout has the same number of samples, but for sequences with different numbers of samples per readout it may be a vector of integers.

# Fields

  * `nreadouts::I`: The total number of readouts for this trajectory
  * `nsamplesperreadout::I`: The total number of samples per readout
  * `Δt::T`: Time between sample points
  * `k_start_readout::U`: Starting position in k-space for each readout
  * `Δk_adc::U`: k-space step Δkₓ per sample point (same for all readouts)
  * `py::V`: Phase encoding index for each readout
  * `readout_oversampling::I`: Readout oversampling factor
