```julia
DOS(Omega::Float64, Ham::Hamiltonian; till_band::Int64=length(Ham.bands[1, 1]), spread::Float64=1e-3) --> Float64
DOS(Omegas::Vector{Float64}, Ham::Hamiltonian; till_band::Int64=length(Ham.bands[1, 1]), spread::Float64=1e-3) --> Vector{Float64}
```

Calculate the Density of State correspondingto the given energies in `Omegas`, for the lowest bands upto `till_band`. The calculation is done at a finite `spread` of the delta-function sum. 
