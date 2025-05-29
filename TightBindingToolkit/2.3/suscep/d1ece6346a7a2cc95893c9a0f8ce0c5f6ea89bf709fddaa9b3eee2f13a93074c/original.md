```julia
FindReducedChi(Q::Vector{Float64}, Omega::Float64 , M::Model; a::Int64=3, b::Int64=3, eta::Float64=1e-2) --> ComplexF64
```

function to calculate susceptibility at a fixed Ω=`Omega`, and `Q`, and along a fixed direction given by `a` and `b`.
