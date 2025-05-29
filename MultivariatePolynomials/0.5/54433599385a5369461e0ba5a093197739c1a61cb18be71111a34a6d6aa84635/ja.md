```
primitive_part(poly::AbstractPolynomialLike{T}, algo::AbstractUnivariateGCDAlgorithm) where {T}
```

多項式 `poly` の *原始部分* を一意因子分解環 `S` 上で返します。これは、[`content`](@ref) による `poly` の正確な除算を返すことを意味します。内容も必要な場合は、代わりに [`primitive_part_content`](@ref) を呼び出してください。

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. 第3版。
