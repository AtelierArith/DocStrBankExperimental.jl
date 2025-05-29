```
Rsymbol(a::I, b::I, c::I) where {I<:Sector}
```

$$
R
$$

-シンボル $R^{ab}_c$ を返します。これは $c → a ⊗ b$ と $c → b ⊗ a$ の間のマッピングを示します。

```
a -<-μ-<- c                                 b -<-ν-<- c
     ∨          -> Rsymbol(a,b,c)[μ,ν]           v
     b                                           a
```

`FusionStyle(I)` が `UniqueFusion()` または `SimpleFusion()` の場合、R-シンボルは数値です。それ以外の場合は、行と列のサイズが `Nsymbol(a,b,c) == Nsymbol(b,a,c)` の正方行列になります。
