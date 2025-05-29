```
spherical_harmonics(l_max::Int, θ::T, φ::T)
```

Returns a vector of all the spherial harmonics $Y_{(l,m)}(\theta,\phi)$ for all the degrees `l` and orders `m`. The degree and order (indices) of the elements of the vector are given by `spherical_harmonics_indices(l_max::Int)`.
