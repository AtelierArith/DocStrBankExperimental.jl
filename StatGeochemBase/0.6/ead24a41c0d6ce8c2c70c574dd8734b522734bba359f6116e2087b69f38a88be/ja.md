```julia
fast_inv_sqrt(x)
```

悪名高い `x` の高速逆平方根で、32ビットおよび64ビットのバージョンがあります。ベースの `1/sqrt(x)` よりも最大10倍速くなる可能性がありますが、精度の非自明な損失があります。ここでの実装は約4ppmの精度があります。
