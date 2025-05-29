function cumfsel(Σ::SymmetricTensor{T,2}, c::SymmetricTensor{T, N}, f::String, k::Int = Σ.dats) where {T <: AbstractFloat, N}

Returns an Array of tuples (ind::Array{Bool}, fval::Float64, i::Int). Given k-th Array ind are marginals removed after k -steps as those with low N'th order dependency, fval, the value of the target function at step k and i, a feature removed at step k.

Uses Σ - the covariance matrix and c - the N'th cumulant tensor to measure the N'th order dependencies between marginals. Function f is the optimization function, ["hosvd", "norm", "mev"] are supported.

```jldoctest

julia> Random.seed!(42);

julia> x = rand(12,10);

julia> c = cumulants(x, 4);

julia> cumfsel(c[2], c[4], "hosvd")
10-element Array{Any,1}:
 (Bool[true, true, true, false, true, true, true, true, true, true], 27.2519, 4)
 (Bool[true, true, false, false, true, true, true, true, true, true], 22.6659, 3)
 (Bool[true, true, false, false, false, true, true, true, true, true], 18.1387, 5)
 (Bool[false, true, false, false, false, true, true, true, true, true], 14.4492, 1)
 (Bool[false, true, false, false, false, true, true, false, true, true], 11.2086, 8)
 (Bool[false, true, false, false, false, true, true, false, true, false], 7.84083, 10)
 (Bool[false, false, false, false, false, true, true, false, true, false], 5.15192, 2)
 (Bool[false, false, false, false, false, false, true, false, true, false], 2.56748, 6)
 (Bool[false, false, false, false, false, false, true, false, false, false], 0.30936, 9)
 (Bool[false, false, false, false, false, false, false, false, false, false], 0.0, 7)
```
