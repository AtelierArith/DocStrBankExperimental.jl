```
@unitgroup(U::UnitSystem,S::UnitSystem) -> (u::typeof(normal(U)))(d::Group) = normal(S)(d)
```

`U`に対する`Group`の準同型を、`S`からの既存の仕様に基づいて実装します。
