```
CoherencyMatrix(s::StokesParams, basis1::PolBasis)
CoherencyMatrix(s::StokesParams, basis1::PolBasis, basis2::PolBasis)
CoherencyMatrix(s::StokesParams, basis1::PolBasis, basis2::PolBasis, refbasis=CirBasis())
```

Constructs the coherency matrix from the set of stokes parameters `s`. This is specialized on `basis1` and `basis2` which form the tensor product basis `|basis1><basis2|`, or if a single basis is given then by `|basis><basis|`.

For example

```julia
CoherencyMatrix(s, CircBasis())
```

will give the coherency matrix

```
   I+V   Q+iU
   Q-iU  I-V
```

while

```julia
CoherencyMatrix(s, LinBasis())
```

will give

```
    I+Q   U+iV
    U-iV  I-Q
```

# Notes

Internally this function first converts to a reference basis and then the final basis. You can select the reference basis used with the optional argument refbasis. By default we use the circular basis as our reference. Note that this is only important for mixed bases, e.g., if `basis1` and `basis2` are different. If `basis1==basis2` then the reference basis is never used.
