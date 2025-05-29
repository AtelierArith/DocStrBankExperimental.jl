```
Rsymbol(a::I, b::I, c::I) where {I<:Sector}
```

Returns the R-symbol $R^{ab}_c$ that maps between $c → a ⊗ b$ and $c → b ⊗ a$ as in

```
a -<-μ-<- c                                 b -<-ν-<- c
     ∨          -> Rsymbol(a,b,c)[μ,ν]           v
     b                                           a
```

If `FusionStyle(I)` is `UniqueFusion()` or `SimpleFusion()`, the R-symbol is a number. Otherwise it is a square matrix with row and column size `Nsymbol(a,b,c) == Nsymbol(b,a,c)`.
