```
model, x0 = subspaceid(data::InputOutputFreqData,
    Ts = data.Ts,
    nx = :auto;
    cont = false,
    verbose = false,
    r = nx === :auto ? min(length(data) ÷ 20, 20) : 2nx, # Internal model order
    zeroD = false,
    estimate_x0 = true,
    stable = true, 
    svd = svd!,
    Aestimator = \,
    Bestimator = \,
    weights = nothing
)
```

Estimate a state-space model using subspace-based identification in the frequency domain.

If results are poor, try modifying `r`, in particular if the amount of data is low.

See the [docs](https://baggepinnen.github.io/ControlSystemIdentification.jl/dev/freq/#Statespace) for an example.

# Arguments:

  * `data`: A frequency-domain identification data object.
  * `Ts`: Sample time at which the data was collected
  * `nx`: Desired model order, an interer or `:auto`.
  * `cont`: Return a continuous-time model? A bilinear transformation is used to convert the estimated discrete-time model, see function `d2c`.
  * `verbose`: Print stuff?
  * `r`: Internal model order, must be ≥ `nx`.
  * `zeroD`: Force the `D` matrix to be zero.
  * `estimate_x0`: Esimation of extra parameters to account for initial conditions. This may be required if the data comes from the fft of time-domain data, but may not be required if the data is collected using frequency-response analysis with exactly periodic input and proper handling of transients.
  * `stable`: For the model to be stable (uses [`schur_stab`](@ref)).
  * `svd`: The `svd` function to use.
  * `Aestimator`: The estimator of the `A` matrix (and initial `C`-matrix).
  * `Bestimator`: The estimator of B/D and C/D matrices.
  * `weights`: An optional vector of frequency weights of the same length as the number of frequencies in `data.
