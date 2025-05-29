```
to_dict(h::BloqadeExpr.RydbergHamiltonian; nshots::Int, device_capabilities::DeviceCapabilities=get_device_capabilities())
to_dict(h::BloqadeExpr.RydbergHamiltonian,params::SchemaTranslationParams)
```

Converts `h` and associated `params` into the dictionary representation of a [`QuEraTaskSpecification`](@ref). If `params` is not explicitly provided as a `SchemaTranslationParams` instance, it is automatically built from `nshots` and `device_capabilities`.

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
