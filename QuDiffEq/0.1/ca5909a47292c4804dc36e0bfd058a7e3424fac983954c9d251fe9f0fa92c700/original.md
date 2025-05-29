```
circuit_ends(n::Int, blk::TaylorParam{CPType, false}, VS1::AbstractMatrix, VT::AbstractMatrix)
```

Generates the part of circuit that computes and decomputes the superposition of the ancilla bits, in non-unitary H `taylorcircuit`
