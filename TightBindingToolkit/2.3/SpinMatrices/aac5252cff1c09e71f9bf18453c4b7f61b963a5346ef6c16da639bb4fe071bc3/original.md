```julia
SpinMats(spin::Rational{Int64}) --> Vector{Matrix{ComplexF64}}
```

Returns the 3 generators of SU(2) in the given spin-representation, along with the Identity matrix of d = 2*spin+1, in the format of [Sx, Sy, Sz, Id]
