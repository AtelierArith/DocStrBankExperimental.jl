```
par(t::TPS, monomialindex)
```

Extracts a polynomial from the TPS containing the specified monomial, and removes the monomial.  Any of the three monomial indexing schemes (by order, sparse monomial, or monomial index –  see the Monomial Indexing section of the GTPSA manual for more details) may be used to specify  the monomial.

# Examples: Variable/Parameter Index:

```julia-repl
julia> d = Descriptor(5, 10, 2, 10); Δx = @vars(d); Δk = @params(d);

julia> f = 2*Δx[1]^2*Δx[3] + 3*Δx[1]^2*Δx[2]*Δx[3]*Δx[4]^2*Δx[5]*Δk[1] + 6*Δx[3] + 5
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  5.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  6.0000000000000000e+00      1      0   0   1   0   0   |   0   0
  2.0000000000000000e+00      3      2   0   1   0   0   |   0   0
  3.0000000000000000e+00      8      2   1   1   2   1   |   1   0


julia> par(f, 3)
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  6.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  2.0000000000000000e+00      2      2   0   0   0   0   |   0   0
  3.0000000000000000e+00      7      2   1   0   2   1   |   1   0


julia> par(f, param=1)
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  3.0000000000000000e+00      7      2   1   1   2   1   |   0   0
```

# Examples: Monomial Index-by-Order

```julia-repl
julia> par(f, [2,:,1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  3.0000000000000000e+00      5      0   1   0   2   1   |   1   0


julia> par(f, [2,0,1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0   0   0   0   |   0   0
```

# Examples: Monomial Index-by-Sparse Monomial

```julia-repl
julia> par(f, [1=>2, 3=>1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  2.0000000000000000e+00      0      0   0   0   0   0   |   0   0
  3.0000000000000000e+00      5      0   1   0   2   1   |   1   0


julia> par(f, params=[1=>1])
TPS64{Descriptor(NV=5, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  3.0000000000000000e+00      7      2   1   1   2   1   |   0   0
```
