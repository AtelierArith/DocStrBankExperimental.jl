```julia
tetunsuitable!(unsuitable; check_signature)

```

Set tetunsuitable function called from C wrapper. Setting this function is valid only for one subsequent call to tetrahedralize. The function to be passed has the signature

```
unsuitable(p1::Vector{Float64},p2::Vector{Float64},p3::Vector{Float64},p4::Vector{Float64})::Bool
```

where `p1...p4` are 3-Vectors describing the corners of a tetrahedron, and the return value is `true` if its volume is seen as too large.
