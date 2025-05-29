```
Bsymbol(a::I, b::I, c::I) where {I<:Sector}
```

Return the value of $B^{ab}_c$ which appears in transforming a splitting vertex into a fusion vertex using the transformation

```
a -<-μ-<- c                                                    a -<-ν-<- c
     ∨          -> √(dim(c)/dim(a)) * Bsymbol(a,b,c)[μ,ν]           ∧
     b                                                            dual(b)
```

If `FusionStyle(I)` is `UniqueFusion()` or `SimpleFusion()`, the B-symbol is a number. Otherwise it is a square matrix with row and column size `Nsymbol(a, b, c) == Nsymbol(c, dual(b), a)`.
