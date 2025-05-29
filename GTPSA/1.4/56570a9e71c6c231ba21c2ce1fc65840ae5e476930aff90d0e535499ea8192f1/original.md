```
deriv(t1::TPS, monomialindex)
∂(t1::TPS, monomialindex)
```

Differentiates `t1` wrt the variable/parameter specified by the variable/parameter index, or  alternatively any monomial specified by indexing-by-order OR indexing-by-sparse monomial.

# Examples: Variable/Parameter Index:

```julia-repl
julia> d = Descriptor(2, 5);

julia> Δx = @vars(d);

julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], 1)
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      0   1


julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], 2)
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      1   0
```

# Examples: Monomial Index-by-Order

```julia-repl
julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [1,0])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      0   1


julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [1,1])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  3.0000000000000000e+00      0      0   0
```

# Examples: Monomial Index-by-Sparse Monomial

```julia-repl
julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [1=>1])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      0   1


julia> deriv(Δx[1] + 2*Δx[2] + 3*Δx[1]*Δx[2], [2=>1])
TPS64{Descriptor(NV=2, MO=5)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0
  3.0000000000000000e+00      1      1   0
```
