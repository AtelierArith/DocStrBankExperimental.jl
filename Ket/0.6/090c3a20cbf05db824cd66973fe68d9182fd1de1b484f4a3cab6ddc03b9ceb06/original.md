```
dilate_povm(E::Vector{<:AbstractMatrix})
```

Does the Naimark dilation of a POVM given as a vector of matrices. This always works, but is wasteful if the POVM elements are not full rank.
