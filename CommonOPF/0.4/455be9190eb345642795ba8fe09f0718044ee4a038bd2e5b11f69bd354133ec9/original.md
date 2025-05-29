```
substation_voltage(net::Network{MultiPhase})::Vector{ComplexF64}
```

Parse `net.v0` into a Vector{ComplexF64}, allowing for `net.v0` to be a `Real`, `AbstractVector{<:Real}`, or `AbstractVector{<:Complex}`.
