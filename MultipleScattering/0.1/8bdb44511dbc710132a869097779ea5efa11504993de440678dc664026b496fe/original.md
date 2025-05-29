`spherical_harmonics(l_max::Int, θ::Complex{T}, φ::Union{T,Complex{T}})`

returns a vector of all spherical harmonics with degree `l <= l_max` with complex arguments. The degree and order (indices) of the elements of the vector are given by `spherical_harmonics_indices(l_max::Int)`.
