```
@tensoropt(optex, block)
@tensoropt(block)
```

Specify one or more tensor operations using Einstein's index notation. Indices can be chosen to be arbitrary Julia variable names, or integers. When contracting several tensors together, the macro will determine (at compile time) the optimal contraction order depending on the cost associated to the individual indices. If no `optex` is provided, all indices are assumed to have an abstract scaling `χ` which is optimized in the asympotic limit of large `χ`.

The cost can be specified in the following ways:

```julia
# cost χ for all indices (a, b, c, d, e, f)
@tensoropt D[a, b, c, d] := A[a, e, c, f] * B[g, d, e] * C[g, f, b]

# asymptotic cost χ for indices (a, b, c, e), other indices (d, f) have cost 1
@tensoropt (a, b, c, e) C[a, b, c, d] := A[a, e, c, f, h] * B[f, g, e, b] * C[g, d, h]

# cost 1 for indices (a, b, c, e); other indices (d, f) have asymptotic cost χ
@tensoropt !(a, b, c, e) C[a, b, c, d] := A[a, e, c, f, h] * B[f, g, e, b] * C[g, d, h]

# cost as specified for listed indices, unlisted indices have cost 1 (any symbol for χ can be used)
@tensoropt (a => χ, b => χ^2, c => 2 * χ, e => 5) begin
    C[a, b, c, d] := A[a, e, c, f, h] * B[f, g, e, b] * C[g, d, h]
end
```

Note that `@tensoropt` will optimize any tensor contraction sequence it encounters in the (block of) expressions. It will however not break apart expressions that have been explicitly grouped with parenthesis, i.e. in

```julia
@tensoropt C[a, b, c, d] := A[a, e, c, f, h] * (B[f, g, e, b] * C[g, d, h])
```

it will always contract `B` and `C` first. For a single tensor contraction sequence, the optimal contraction order and associated (asymptotic) cost can be obtained using `@optimalcontractiontree`.
