```
primitive_part_content(poly::AbstractPolynomialLike{T}, algo::AbstractUnivariateGCDAlgorithm) where {T}
```

多項式 `poly` の *原始部分* と *内容* を一意因子分解環 `S` 上で返します。これは [Knu14, (3) p. 423] で定義されています。この関数を呼び出す方が [`primitive_part`](@ref) と [`content`](@ref) を別々に呼び出すよりも効率的です。なぜなら、原始部分を計算するにはまず内容を計算する必要があり、この関数は内容を二度計算することを避けるからです。

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. 第3版。
