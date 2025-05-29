```
cormatgen(n::Int = 20)
```

Returns symmetric correlation matrix Σ of size n x n. Method:

```
a = rand(n,n)
b = a*a'
c = b./maximum(b)
```

Example:

```jldoctest
julia> Random.seed!(43);

julia> cormatgen(2)
2×2 Array{Float64,2}:
 1.0       0.660768
 0.660768  1.0
```
