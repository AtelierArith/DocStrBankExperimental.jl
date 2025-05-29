```
characteristic_polynomial(M::Matroid)
characteristic_polynomial(M::Matroid; parent::ZZPolyRing)
characteristic_polynomial(parent::ZZPolyRing, M::Matroid)
```

`M`の特性多項式を返します。これは整数係数の変数qに関する多項式です。これはTutte多項式の評価として計算されます。[Oxl11](@cite)のセクション15.2を参照してください。

# 例

```jldoctest
julia> characteristic_polynomial(fano_matroid())
q^3 - 7*q^2 + 14*q - 8

```
