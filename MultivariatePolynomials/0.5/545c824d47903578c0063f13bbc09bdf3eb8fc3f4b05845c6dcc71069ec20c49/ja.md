```
coefficient_type(p::AbstractPolynomialLike)
```

`p`の係数の型を返します。

```
coefficient_type(::Type{PT}) where PT
```

型`PT`の多項式の係数の型を返します。

### 例

$$
(4//5)x^2y
$$

に対して`coefficient_type`を呼び出すと`Rational{Int}`が返され、$1.0x^2y + 2.0x$に対して`coefficient_type`を呼び出すと`Float64`が返され、$xy$に対して`coefficient_type`を呼び出すと`Int`が返されるべきです。
