```
bvec(p::Polynomial{F2,:x}, bw::Int=0)::Vector{F2}
```

Convert a polynomial over F2 to its binary vector representation.

# Arguments

  * `p::Polynomial{F2,:x}`: A polynomial over F2
  * `bw::Int`: Optional bit width (default: 0, meaning use polynomial degree)

# Returns

  * `Vector{F2}`: Binary vector representation of the polynomial
