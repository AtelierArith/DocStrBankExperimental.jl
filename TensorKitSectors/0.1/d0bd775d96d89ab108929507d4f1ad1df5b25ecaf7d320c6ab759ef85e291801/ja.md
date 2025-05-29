```
Fsymbol(a::I, b::I, c::I, d::I, e::I, f::I) where {I<:Sector}
```

出力セクター `d` へのセクター `a`、`b`、`c` の2つの異なる融合順序を関連付けるF-シンボル $F^{abc}_d$ を返します。これは、中間セクター $a ⊗ b → e$ または $b ⊗ c → f$ を使用します：

```
a-<-μ-<-e-<-ν-<-d                                     a-<-λ-<-d
    ∨       ∨       -> Fsymbol(a,b,c,d,e,f)[μ,ν,κ,λ]      ∨
    b       c                                             f
                                                          v
                                                      b-<-κ
                                                          ∨
                                                          c
```

`FusionStyle(I)` が `UniqueFusion` または `SimpleFusion` の場合、F-シンボルは数値です。それ以外の場合、F-シンボルはサイズ `(Nsymbol(a, b, e), Nsymbol(e, c, d), Nsymbol(b, c, f), Nsymbol(a, f, d))` のランク4の配列です。
