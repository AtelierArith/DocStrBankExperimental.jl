```
mindegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}})
```

`p`の単項式の最小総次数を返します。すなわち、`minimum(degree, terms(p))`です。

```
mindegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}}, v::AbstractVariable)
```

変数`v`における`p`の単項式の最小次数を返します。すなわち、`minimum(degree.(terms(p), v))`です。

### 例

$$
4x^2y + xy + 2x
$$

に対して`mindegree`を呼び出すと1が返され、`mindegree(4x^2y + xy + 2x, x)`は1を返し、`mindegree(4x^2y + xy + 2x, y)`は0を返します。
