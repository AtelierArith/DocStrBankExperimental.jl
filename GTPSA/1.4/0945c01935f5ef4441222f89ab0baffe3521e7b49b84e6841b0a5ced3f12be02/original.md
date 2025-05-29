```
mono([tpstype, ] monomialindex [, use=(descriptor|tps)])
```

Returns a `TPS` of type `tpstype` (which defaults to `TPS{Float64,GTPSA.Dynamic}`) with  the specified monomial set to 1. Any of the three monomial indexing schemes (by order, sparse  monomial, or monomial index – see the Monomial Indexing section of the GTPSA manual for more  details) may be used to specify the monomial to set to one. E.g. a call to this function is  equivalent to doing `t = (tpstype)(use=use); t[monomialindex] = 1`

`use` may only be specified if `tpstype <: TPS{T where {T},<:GTPSA.Dynamic}`.

# Examples: Variable/Parameter Index:

```julia-repl
julia> d = Descriptor(3,10,2,10);

julia> mono(1)
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      1   0   0   |   0   0


julia> mono(ComplexTPS64, 1)
ComplexTPS64{GTPSA.Dynamic}:
 Real                     Imag                       Order   Exponent
  1.0000000000000000e+00   0.0000000000000000e+00      1      1   0   0   |   0   0


julia> mono(ComplexTPS64{d}, param=2)
ComplexTPS64{Descriptor(NV=3, MO=10, NP=2, PO=10)}:
 Real                     Imag                       Order   Exponent
  1.0000000000000000e+00   0.0000000000000000e+00      1      0   0   0   |   0   1
```

# Examples: Monomial Index-by-Order

```julia-repl
julia> mono([1,2,3])
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      6      1   2   3   |   0   0


julia> mono([0,0,3,2,1], use=d)
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      6      0   0   3   |   2   1


julia> mono(TPS64{d}, [1,0,0,0,1])
TPS64{Descriptor(NV=3, MO=10, NP=2, PO=10)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      2      1   0   0   |   0   1
```

# Examples: Monomial Index-by-Sparse Monomial

```julia-repl
julia> mono([1=>1])
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      1   0   0   |   0   0


julia> mono([2=>1])
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      0   1   0   |   0   0


julia> mono([1=>1], params=[2=>1], use=d)
TPS64{GTPSA.Dynamic}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      2      1   0   0   |   0   1
```
