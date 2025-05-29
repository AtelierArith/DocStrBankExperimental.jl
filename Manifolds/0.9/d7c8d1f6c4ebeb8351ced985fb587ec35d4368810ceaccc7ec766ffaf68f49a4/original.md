```
Y = project(M::SPDFixedDeterminant, p, X)
project!(M::SPDFixedDeterminant, Y, p, X)
```

Project the symmetric matrix `X` onto the tangent space at `p` of the (sub-)manifold of s.p.d. matrices of determinant `M.d` (in place of `Y`), by setting its diagonal (and hence its trace) to zero.
