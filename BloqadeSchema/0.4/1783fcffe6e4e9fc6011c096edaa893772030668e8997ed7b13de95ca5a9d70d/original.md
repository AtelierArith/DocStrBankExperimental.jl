```
to_json(h::AbstractBlock; kw...)
to_json(h::BloqadeExpr.RydbergHamiltonian,params::SchemaTranslationParams)
```

Converts `h` and associated `params` into a JSON object. If `params` is not explicitly provided as a `SchemaTranslationParams` instance, it is automatically built from `nshots` and `device_capabilities`.

Validation is performed to ensure `h` is capable of being run on the machine. This can cause an exception to be thrown should any violations be caught. Refer to Logs/Warnings/Exceptions below.

# Logs/Warnings/Exceptions

A `ValidationException` can be thrown which wraps a [`ValidationViolations`](@ref) instance.

`ValidationViolations` contains any constraint violations detected from [`to_schema`](@ref)

Violations include:

## Waveform Type

  * ϕ is not of type `PiecewiseConstantWaveform`
  * Ω and Δ are not of type `PiecewiseLinearWaveform`

## Atom Position

  * Number of qubits requested exceeds what is supported by the device
  * Atom positions exceed position resolution supported by the device
  * The total width/height of the atom arrangement exceeds what is supported by the device
  * The radial spacing between atoms is smaller than what is supported by the device
  * The vertical row spacing between atoms is smaller than what is supported by the device

## General Waveform Constraints (apply to Ω, Δ, ϕ)

  * duration exceeds device supported duration
  * duration is smaller than device supported minimum time step
  * smallest time step is smaller than supported smallest time step
  * value is smaller than smallest supported value
  * value is larger than largest supported value

## Ω Waveform specific constraints

  * Slope exceeds largest supported slope
  * Start and end values are not equal to 0.0 rad/μs

## Δ Waveform specific constraints

  * Slope exceeds largest supported slope

## ϕ Waveform specific constraints

  * start value is not equal to 0.0 rad/μs

## Miscellaneous Violations

  * Number of shots is below minimum supported
  * Number of shots exceeds maximum supported

# Examples

```jldoctest
julia> Ω = BloqadeWaveforms.piecewise_constant(; clocks=[0, 2, 4, 6, 7], values=[5, 3, 4, 6]);

julia> Δ = BloqadeWaveforms.piecewise_linear(; clocks=[0.0, 0.6, 2.1, 2.2], values=[-10.1, -10.1, 10.1, 10.1]);

julia> ϕ = BloqadeWaveforms.piecewise_linear(; clocks=[0, 5], values=[33, 0]);

julia> atoms = [(0, 0), (1, 3), (4, 2), (6, 3), (0, 5), (2, 5)];

julia> block = BloqadeExpr.rydberg_h(atoms; Δ=Δ, Ω=Ω, ϕ=ϕ);

julia> BloqadeSchema.to_json(block; n_shots=10)
"{"nshots":10,"lattice":{"sites":[[0.0,0.0],[1.0,3.0],[4.0,2.0],[6.0,3.0],[0.0,5.0],[2.0,5.0]],"filling":[1,1,1,1,1,1]},"effective_hamiltonian":{"rydberg":{"rabi_frequency_amplitude":{"global":{"times":[0.0,-18.0,2.0,-6.0,4.0,-14.0,7.0],"values":[5.0,5.0,3.0,3.0,4.0,4.0,6.0]}},"rabi_frequency_phase":{"global":{"times":[0.0,5.0],"values":[33.0,0.0]}},"detuning":{"global":{"times":[0.0,0.6,2.1,2.2],"values":[-10.1,-10.1,10.1,10.1]}}}}}"
```
