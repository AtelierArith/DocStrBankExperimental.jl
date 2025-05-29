```
ProjectedF{A, B}(fnlm::Matrix{A}, lm, radial_basis::B)
```

Stores the $\langle f | n \ell m \rangle$ coefficients and the radial basis that was used to calculate them. It is assumed that spherical harmonics were  used for the angular parts. `A` is the element type of the matrix that stores  `fnlm` coefficients (should be either `Float64` or `Measurement`). `B` is the  type of radial basis. `lm` stores a vector of `(ell,m)` for the `fnlm` matrix: `fnlm` is indexed as `[n+1,i]` corresponding to `(ell,m) = lm[i]`
