```
univariate_gcd(p1::AbstractPolynomialLike, p2::AbstractPolynomialLike, algo::AbstractUnivariateGCDAlgorithm)
```

多項式 `p1` と `p2` の *最大公約数* を返します。これらの多項式は共通の変数を最大1つ持ち、係数は `AbstractFloat` であるか、ユニーク因数分解整域の一部である必要があります。例えば、有理数、整数、または多変数多項式です。したがって、`p1` と `p2` は共通の変数を最大1つ持つべきですが、係数は任意の数の変数を共有する多変数多項式であっても構いません。

係数が `AbstractFloat` でない場合、これにより

1. [`content`](@ref) と [`primitive_part`](@ref) を [`primitive_part_content`](@ref) を使用して `p1` と `p2` を分離します。詳細は [Knu14, Algorithm E: E1, p. 426] または [Knu14, Algorithm C: C1, p. 428] を参照してください。
2. [`gcd`](@ref) を内容と原始部分の間で計算し、原始部分には [`primitive_univariate_gcd!`](@ref) を使用します。
3. これら2つの `gcd` の積を返します。詳細は [Knu14, Algorithm E: E4, p. 427] または [Knu14, Algorithm C: C4, p. 429] を参照してください。

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. 第3版。
