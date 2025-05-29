```
     exponential_part(zs::Vector{Vector{ComplexF64}},
                      Ω::Matrix{ComplexF64})::Vector{Float64}
```

Return the value of the exponential part of the Riemann theta function for Ω and all z in `zs`.

## Parameters

  * `zs` : A vector of complex vectors at which to evaluate the Riemann theta function.
  * `Omega` : A Riemann matrix.

## Returns

The value of the exponential part of the Riemann theta function at each point appearing in `zs`.
