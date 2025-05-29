```
Sweeps(d::AbstractMatrix)

Sweeps(nsweep::Int, d::AbstractMatrix)
```

Make a sweeps object from a matrix of input values. The first row should be strings that define which variables are being set ("maxdim", "cutoff", "mindim", and "noise").

If the number of sweeps are not specified, they are determined from the size of the input matrix.

# Examples

```julia
julia > Sweeps(
  [
    "maxdim" "mindim" "cutoff" "noise"
    50 10 1e-12 1E-7
    100 20 1e-12 1E-8
    200 20 1e-12 1E-10
    400 20 1e-12 0
    800 20 1e-12 1E-11
    800 20 1e-12 0
  ],
)
Sweeps
1cutoff = 1.0E-12, maxdim = 50, mindim = 10, noise = 1.0E-07
2cutoff = 1.0E-12, maxdim = 100, mindim = 20, noise = 1.0E-08
3cutoff = 1.0E-12, maxdim = 200, mindim = 20, noise = 1.0E-10
4cutoff = 1.0E-12, maxdim = 400, mindim = 20, noise = 0.0E+00
5cutoff = 1.0E-12, maxdim = 800, mindim = 20, noise = 1.0E-11
6cutoff = 1.0E-12, maxdim = 800, mindim = 20, noise = 0.0E+00
```
