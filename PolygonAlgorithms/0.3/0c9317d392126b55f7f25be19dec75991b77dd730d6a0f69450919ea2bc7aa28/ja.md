```
xor_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=WeilerAthertonAlg())
```

多角形のxorの一般的なケース：一方の多角形または他方の多角形に存在するが、両方には存在しない。穴を返す可能性があるが、それらを穴として分類しない。

`alg` は `MartinezRuedaAlg()` のみ使用できます。
