`complex_legendre_array(l_max::Int, z::Complex{T})`

returns a vector of all associated legendre functions with degree `l <= l_max`. The degree and order (indices) of the elements of the vector are given by `spherical_harmonics_indices(l_max::Int)`.

The associated legendre polynomials are taken from the package AssociatedLegendrePolynomials.jl.
