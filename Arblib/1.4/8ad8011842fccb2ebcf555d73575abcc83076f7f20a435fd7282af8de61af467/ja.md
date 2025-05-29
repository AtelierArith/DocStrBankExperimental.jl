```
abs_lbound([T, ] x::Union{ArbOrRef,AcbOrRef})
```

`abs(x)`の下限を`Arf`として返します。`T`が指定されている場合はこの型に変換し、`Arf`と`Arb`をサポートします。

`x`に`NaN`が含まれている場合は`NaN`を返します。
