```
content(poly::AbstractPolynomialLike{T}, algo::AbstractUnivariateGCDAlgorithm, mutability::MA.MutableTrait) where {T}
```

多項式 `poly` の *content* を一意因子分解環 `S` 上で返します。これは、`poly` の係数の `gcd` を返すことを意味します。詳細は [`primitive_part_content`](@ref) を参照してください。

出力は、`mutability` が `MA.IsNotMutable` の場合、`poly` に影響を与えずに変更可能です。

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. 第3版。
