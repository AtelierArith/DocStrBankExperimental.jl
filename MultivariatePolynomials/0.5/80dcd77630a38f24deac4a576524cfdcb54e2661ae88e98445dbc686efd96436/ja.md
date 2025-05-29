```
isolate_variable(poly::_APL, var::AbstractVariable, mutability::MA.MutableTrait)
```

変数 `var` を持つ多項式を返します。`poly` の他の変数は係数として移動されます。

出力は、`mutability` が `MA.IsNotMutable` の場合、`poly` に影響を与えることなく変更できます。
