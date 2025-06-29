[`Kahan` matrix](https://math.nist.gov/MatrixMarket/data/MMDELI/kahan/kahan.html)

```jldoctest
julia> A = Kahan(5,5,1,35)
5×5 Kahan{Int64, Int64}:
 1.0  -0.540302  -0.540302  -0.540302  -0.540302
 0.0   0.841471  -0.454649  -0.454649  -0.454649
 0.0   0.0        0.708073  -0.382574  -0.382574
 0.0   0.0        0.0        0.595823  -0.321925
 0.0   0.0        0.0        0.0        0.501368

julia> A = Kahan(5,3,0.5,0)
5×3 Kahan{Float64, Int64}:
 1.0  -0.877583  -0.877583
 0.0   0.479426  -0.420735
 0.0   0.0        0.229849
 0.0   0.0        0.0
 0.0   0.0        0.0

julia> A = Kahan(3,5,0.5,1e-3)
3×5 Kahan{Float64, Float64}:
 1.0  -0.877583  -0.877583  -0.877583  -0.877583
 0.0   0.479426  -0.420735  -0.420735  -0.420735
 0.0   0.0        0.229849  -0.201711  -0.201711
```

For more details see: N. Higham, "A Survey of Condition Number Estimation for Triangular Matrices," SIMAX, Vol. 29, No. 4, pp. 588, 1987, https://doi.org/10.1137/1029112
