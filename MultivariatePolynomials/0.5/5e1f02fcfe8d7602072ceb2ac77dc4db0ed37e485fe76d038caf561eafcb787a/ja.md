```
maxdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

`p`の単項式の最大総次数を返します。すなわち、`maximum(degree, terms(p))`です。

```
maxdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

変数`v`における`p`の単項式の最大次数を返します。すなわち、`maximum(degree.(terms(p), v))`です。

### 例

$$
4x^2y + xy + 2x
$$

に対して`maxdegree`を呼び出すと3が返され、`maxdegree(4x^2y + xy + 2x, x)`は2を返し、`maxdegree(4x^2y + xy + 2x, y)`は1を返します。
