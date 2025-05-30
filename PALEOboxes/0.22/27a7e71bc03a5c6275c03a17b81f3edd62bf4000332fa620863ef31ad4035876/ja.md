```
AbstractIsotopeScalar <: AbstractData
```

IsotopeScalarは同位体組成を持つ量またはフラックスを表します。スカラーと加算、減算、乗算が可能で、同じ（バルク）輸送特性を持つ成分に分解できます。

# 実装

各IsotopeScalarは`IsotopeTypes`に追加され、以下を実装する必要があります：

  * get_total(is::IsotopeScalar) -> total
  * 算術演算 +/-（つまりIsotopeScalarは加算および減算が可能）および *number, /number（IsotopeScalarは実数でスケーリング可能）。
  * [`AbstractData`](@ref) インターフェースのメソッド

およびオプションの同位体特有の関数、例えば単一の同位体の場合：

  * isotope_totaldelta(::Type{<: IsotopeScalar}, total, delta) -> IsotopeScalar()
  * get_delta(is::IsotopeScalar) -> delta
