```
levinson(r::AbstractVector, b::AbstractVector)
```

`x = T \ b` を解きます。ここで `T = SymmetricToeplitz(vcat(1, r))` であり、すなわち `T_{ij} = r[abs(i-j)]` です。仮定として `r[0] = 1` であり、`T` は正定値です。
