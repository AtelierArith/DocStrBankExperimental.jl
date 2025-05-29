```
Fsymbol(a::I, b::I, c::I, d::I, e::I, f::I) where {I<:Sector}
```

Return the F-symbol $F^{abc}_d$ that associates the two different fusion orders of sectors `a`, `b` and `c` into an ouput sector `d`, using either an intermediate sector $a ⊗ b → e$ or $b ⊗ c → f$:

```
a-<-μ-<-e-<-ν-<-d                                     a-<-λ-<-d
    ∨       ∨       -> Fsymbol(a,b,c,d,e,f)[μ,ν,κ,λ]      ∨
    b       c                                             f
                                                          v
                                                      b-<-κ
                                                          ∨
                                                          c
```

If `FusionStyle(I)` is `UniqueFusion` or `SimpleFusion`, the F-symbol is a number. Otherwise it is a rank 4 array of size `(Nsymbol(a, b, e), Nsymbol(e, c, d), Nsymbol(b, c, f), Nsymbol(a, f, d))`.
