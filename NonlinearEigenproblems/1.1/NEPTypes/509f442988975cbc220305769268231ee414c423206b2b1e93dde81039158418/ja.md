```
function estimate_error(E::ErrmeasureType,λ,v)
```

固有対 `(λ,v)` の誤差推定値を返します。誤差を測定する方法は `E` で指定され、`Errmeasure` または `Function` であることができます。

参照: [`Errmeasure`](@ref), [`ErrmeasureType`](@ref)
