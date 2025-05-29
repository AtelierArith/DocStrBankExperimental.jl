```
polynomial(p::AbstractPolynomialLike)
```

`p`を多項式型の値に変換します。

```
polynomial(p::AbstractPolynomialLike, ::Type{T}) where T
```

`p`を係数型`T`の多項式型の値に変換します。

```
polynomial(a::AbstractVector, mv::AbstractVector{<:AbstractMonomialLike})
```

`dot(a, mv)`に等しい多項式を作成します。

```
polynomial(terms::AbstractVector{<:AbstractTerm}, s::ListState=MessyState())
```

`terms`が状態`s`にあることが保証されている場合、`sum(terms)`に等しい多項式を作成します。

```
polynomial(f::Function, mv::AbstractVector{<:AbstractMonomialLike})
```

`sum(f(i) * mv[i] for i in 1:length(mv))`に等しい多項式を作成します。

### 例

`polynomial([2, 4, 1], [x, x^2*y, x*y])`を呼び出すと、$4x^2y + xy + 2x$を返すべきです。
