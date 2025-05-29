```
cormatgen_constant(n::Int, α::Real)
```

定数相関行列を返します。定数相関は 0 <= α <= 1 です。

```julia
julia> cormatgen_constant(2, 0.5)
2×2 Array{Real,2}:
 1.0  0.5
 0.5  1.0
```
