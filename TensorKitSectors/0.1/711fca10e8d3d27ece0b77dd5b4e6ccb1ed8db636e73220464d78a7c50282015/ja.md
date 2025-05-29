```
Bsymbol(a::I, b::I, c::I) where {I<:Sector}
```

$$
B^{ab}_c
$$

の値を返します。これは、分割頂点を融合頂点に変換する際に現れる変換を使用して得られます。

```
a -<-μ-<- c                                                    a -<-ν-<- c
     ∨          -> √(dim(c)/dim(a)) * Bsymbol(a,b,c)[μ,ν]           ∧
     b                                                            dual(b)
```

`FusionStyle(I)`が`UniqueFusion()`または`SimpleFusion()`の場合、B-symbolは数値です。それ以外の場合、B-symbolは行と列のサイズが`Nsymbol(a, b, c) == Nsymbol(c, dual(b), a)`の正方行列です。
