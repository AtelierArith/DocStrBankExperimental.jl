```julia
GetCount(Es::Vector{Float64}, mu::Float64, T::Float64, stat::Int64) --> Matrix{Float64}
```

Function to return a diagonal matrix whose entries are M[i, i] = θ(-(E^i(k)-μ)) ––> 1 if the energy is below the chemical potential, otherwise 0.
