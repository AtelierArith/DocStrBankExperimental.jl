```
GenericProd
```

`GenericProd`は`prod`関数の戦略の1つです。この戦略は、閉じた形の積が利用できない場合でも常に結果を生成し、その場合は単に`ProductOf`オブジェクトを返します。`GenericProd`は、状況に応じて`default_prod_rule`にフォールバックすることがあります。たとえば、`default_prod_rule`が`ClosedProd`である場合、`GenericProd`は解析的な閉じた解を使用してツリーを最適化しようとします（可能な場合）。

参照: [`prod`](@ref), [`ProductOf`](@ref), [`ClosedProd`](@ref), [`PreserveTypeProd`](@ref), [`default_prod_rule`](@ref)
