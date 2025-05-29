```
QKModel(state::StateParams, meas::MeasParams; check_stability::Bool=false)
```

Alternative constructor for QKModel that takes pre-built state and measurement parameter objects.

# Arguments

  * `state::StateParams`: State parameters object containing N, mu, Phi, and Omega
  * `meas::MeasParams`: Measurement parameters object containing M, A, B, C, D, and alpha

# Keyword Arguments

  * `check_stability::Bool=false`: If true, checks if the state transition dynamics are stable

# Returns

Returns a QKModel object by unpacking the parameters and calling the primary constructor.

# Example

```julia
# Create parameter objects
state = StateParams(2, [0.0, 0.0], [0.9 0.0; 0.0 0.9], [0.1 0.0; 0.0 0.1])
meas = MeasParams(1, 2, [0.0], [1.0 1.0], [reshape([1.0 0.0; 0.0 1.0], 2, 2)], [0.1], [0.0])

# Create model
model = QKModel(state, meas)
```

See also: `QKModel`, `StateParams`, `MeasParams`
