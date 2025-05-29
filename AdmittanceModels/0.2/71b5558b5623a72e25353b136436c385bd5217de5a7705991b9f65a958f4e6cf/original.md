```
TransmissionLine(ports::Vector{String}, propagation_speed::Float64,
    characteristic_impedance::Float64, len::Float64,
    locations::AbstractVector{Float64}, δ::Float64)
TransmissionLine(ports::Vector{String}, propagation_speed::Real,
    characteristic_impedance::Real, len::Real; locations::Vector{<:Real}=Float64[],
    δ::Real=len/100)
```

A transmission line with given propagation speed and characteristic impedance. Ports will be present at the two ends of the transmission line in addition to the `locations`. `δ` is the maximum length of an LC stage in the circuit approximation to a transmission line. It is ignored when constructing a Blackbox from a TransmissionLine.
