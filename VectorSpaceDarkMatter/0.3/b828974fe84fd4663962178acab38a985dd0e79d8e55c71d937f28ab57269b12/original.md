```
FCoeffs{A, B}(fnlm::Dict{Tuple{Int64,Int64,Int64}, A},
    radial_basis::B)
```

Stores the $\langle f | n \ell m \rangle$ coefficients as a dictionary with `(n,ell,m) => f_nlm` and the radial basis that was used to calculate them. It is assumed that spherical harmonics were used for the angular parts. `A` is  the element type of the dict that stores `fnlm` coefficients (should  be either `Float64` or `Measurement`). `B` is the type of radial basis.
