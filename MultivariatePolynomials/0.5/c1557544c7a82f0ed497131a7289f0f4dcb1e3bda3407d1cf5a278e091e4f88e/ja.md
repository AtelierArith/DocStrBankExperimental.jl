```
variable(p::AbstractPolynomialLike)
```

`p`を変数に変換します。可能でない場合は`InexactError`をスローします。

### 例

`variable(x^2 + x - x^2)`を呼び出すと変数`x`が返され、`variable(1.0y)`を呼び出すと変数`y`が返されますが、`variable(2x)`や`variable(x + y)`を呼び出すと`InexactError`がスローされます。

### 注意

この操作は、`nvariables(p) > 1`の場合、TypedPolynomialsの実装では型が安定していませんが、DynamicPolynomialsでは型が安定しています。
