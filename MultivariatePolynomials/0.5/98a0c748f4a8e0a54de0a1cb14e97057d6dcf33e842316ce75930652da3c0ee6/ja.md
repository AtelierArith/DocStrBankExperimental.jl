```
variable_union_type(p::AbstractPolynomialLike)
```

`p`の変数のスーパタイプを返します。`p`が変数である場合、それは`p`の型ではなく、作成可能なすべての変数のスーパタイプであるべきです。

### 例

`TypedPolynomials`の場合、名前が`x`の変数は型`Variable{:x}`を持つため、`variable_union_type`は`Variable`を返すべきです。`DynamicPolynomials`の場合、すべての変数は同じ型`Variable{C}`を持ち、ここで`C`は可換変数の場合は`true`、非可換変数の場合は`false`ですので、`variable_union_type`は`Variable{C}`を返すべきです。
