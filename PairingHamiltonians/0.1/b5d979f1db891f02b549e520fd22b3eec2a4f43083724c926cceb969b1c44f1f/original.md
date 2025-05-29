```
eval_Hamil(method::String, basis::Vector{Int}, eps::Vector{Float64}, g::Float64, Nq::Int, degenerate::Bool; debug_mode::Int=0, sparce_rep::Bool=false)::Tuple{Matrix{Float64}, Matrix{Float64}, Union{Matrix{Float64}, Dict{UInt64, Float64}}}
```

Function to evaluate the Hamiltonian matrix elements. Once the number of orbitals and the number of occupied states are given, one can prepare the Hamiltonian matrix elements in the full matrix representation or sparse representation. For larger systems, sparse representation using `Dict{UInt64, Float64}` is used instead of storing the full matrix. The keys of the dictionary correspond to the integer representation of many-body configurations.

Note that `"1"` and `'1'` are different in Julia. The former is a string, while the latter is a character.
