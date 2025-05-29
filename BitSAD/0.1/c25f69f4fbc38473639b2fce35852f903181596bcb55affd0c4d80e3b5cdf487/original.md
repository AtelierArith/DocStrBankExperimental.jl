```
SBitstream(value::Real)
SBitstream{T<:Real}(value)
```

A stochastic bitstream that represents a real (floating-point) number between [-1, 1].

Fields:

  * `bits::Vector{SBit}`: the underlying bitstream
  * `value::Float64`: the underlying floating-point number being represented
