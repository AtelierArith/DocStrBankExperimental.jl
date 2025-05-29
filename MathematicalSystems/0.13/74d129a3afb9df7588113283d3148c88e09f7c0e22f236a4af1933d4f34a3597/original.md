```
noise_matrix(s::AbstractSystem)
```

Returns the noise matrix of a system with linear noise.

### Notes

The noise matrix is the matrix proportional to the noise, e.g. the matrix `D` in the linear system with noise, $x' = Ax + Dw$.
