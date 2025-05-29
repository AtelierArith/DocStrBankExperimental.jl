```
PreserveTypeProd{T}
```

`PreserveTypeProd` は `prod` 関数の戦略の一つです。この戦略は、prod の出力が特定の形式であることを制約します。デフォルトでは、`default_prod_rule` からの戦略を使用し、出力を事前に指定された型に変換しますが、いくつかの分布に対してはパフォーマンス向上のために上書きすることができます。

参照: [`prod`](@ref), [`ClosedProd`](@ref), [`PreserveTypeLeftProd`](@ref), [`PreserveTypeRightProd`](@ref), [`GenericProd`](@ref)
