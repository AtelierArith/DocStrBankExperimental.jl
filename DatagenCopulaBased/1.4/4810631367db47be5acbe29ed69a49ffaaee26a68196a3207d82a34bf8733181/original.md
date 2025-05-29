```
cormatgen_rand(n::Int = 20)
```

Returns symmetric correlation matrix Σ of size n x n. Method:

```
a = rand(n,n)
b = a*a'
diagb = Matrix(Diagonal(1 ./sqrt.(LinearAlgebra.diag(b))))
b = diagb*b*diagb
```

In general gives higher correlations than the cormatgen(). Example:

```jldoctest
julia> Random.seed!(43);

julia> cormatgen_rand(2)
2×2 Array{Float64,2}:
 1.0       0.879086
 0.879086  1.0
```
