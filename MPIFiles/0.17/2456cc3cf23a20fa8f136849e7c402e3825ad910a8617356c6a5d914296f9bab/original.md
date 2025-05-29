```julia
mutable struct TransferFunction
```

  * `freq::Vector{Float64}`
  * `data::Matrix{ComplexF64}`
  * `interpolator::Vector{Interpolations.AbstractInterpolation}`
  * `inductionFactor::Vector{Float64}`
  * `units::Vector{Unitful.FreeUnits}`

```
TransferFunction(freq::Vector, data::Array, [phasedata]; [inductionFactor], [units])
```

Create a `TransferFunction` from a data array `data` at frequencies `freq`. `freq` is given in Hz or should have a Unitful frequency unit attached `data` should have the shape [frequencies, channels]. `data` can be either complex or real, if `data` is real a second array `phasedata` can be passed representing the phase in radians. Both the amplitude and the phase can have Unitful units.

# Optional Keyword-Arguments:

  * `inductionFactor::Vector{<:Real}`: induction factor for each channel
  * `units::Vector`: units for each channel, can be either Unitful.FreeUnits or a string that can be parsed as a Unitful unit. Instead of using this keyword, `data` can also have Unitful units attached, then the units keyword-argument is ignored.
