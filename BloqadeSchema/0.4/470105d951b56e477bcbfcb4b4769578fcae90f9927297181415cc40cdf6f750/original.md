```
validate(H::BloqadeExpr.RydbergHamiltonian;device_capabilities::DeviceCapabilities=get_device_capabilities())
```

Checks if `H` is capable of being represented as part of the internal schema as well as if it falls in the capabilities of what the machine can do via `device_capabilities`.

Returns [`ValidationViolations`](@ref) with each field containing a set of strings indicating which constraints were violated for which part of `H`.

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

# Logs/Warnings/Exceptions

The following exceptions can be thrown:

  * ϕ is not of type `PiecewiseConstantWaveform`
  * Ω and Δ are not of type `PiecewiseLinearWaveform`

# Examples

```jldoctest; setup:=(using BloqadeExpr, BloqadeWaveforms, BloqadeLattices)
julia> Δ = Ω = ϕ = sinusoidal(duration=2, amplitude=1.3*π);

julia> h = rydberg_h(atom_positions; Ω=Ω,Δ=Δ,ϕ=ϕ)

julia> transformed_h, _ = transform(h); # transform returns error info

julia> validate(transformed_h) # constrained by default value of `device_capabilities` argument
The following validation violations occurred:

1. positions 2 => (2.0, 0.0) and 3 => (3.0, 0.0) are a distance of 1.0 μm apart which is below minimum value of 4.0 μm
2. positions 1 => (1.1, 0.0) and 2 => (2.0, 0.0) are a distance of 0.8999999999999999 μm apart which is below minimum value of 4.0 μm
3. positions 1 => (1.1, 0.0) and 3 => (3.0, 0.0) are a distance of 1.9 μm apart which is below minimum value of 4.0 μm
```
