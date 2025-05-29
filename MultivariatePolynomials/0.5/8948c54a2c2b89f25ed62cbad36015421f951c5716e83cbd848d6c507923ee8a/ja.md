```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}})
```

`p`の単項式の極値の総次数を返します。すなわち、`(mindegree(p), maxdegree(p))`です。

```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}}, v::AbstractVariable)
```

変数`v`における`p`の単項式の極値の次数を返します。すなわち、`(mindegree(p, v), maxdegree(p, v))`です。

### 例

$$
4x^2y + xy + 2x
$$

に対して`extdegree`を呼び出すと`(1, 3)`が返され、`extdegree(4x^2y + xy + 2x, x)`は`(1, 2)`を返し、`maxdegree(4x^2y + xy + 2x, y)`は`(0, 1)`を返します。
