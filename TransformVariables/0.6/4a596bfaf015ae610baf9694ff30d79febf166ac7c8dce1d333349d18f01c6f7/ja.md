`transform(t, x)`

`t`を使って`x`を変換します。

`transform(t)`。

引数を変換する`x -> transform(t, x)`に相当する呼び出し可能なものを返します：

```julia
transform(t, x) == transform(t)(x)
```
