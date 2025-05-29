```
number_field(f::QQPolyRingElem, s::VarName;
            cached::Bool = true, check::Bool = true)
```

与えられた多項式 $f$ に対して、数体 $\mathbb{Q}[x]/(f)$ の親オブジェクト $R$ と生成元 $x$ からなるタプル $R, x$ を返します。与えられた文字列 `s` は、数体の生成元がどのように印刷されるべきかを指定します。`s` が指定されていない場合、デフォルトは `_a` です。

# 例

```jldoctest
julia> R, x = polynomial_ring(QQ, "x");

julia> K, a = number_field(x^3 + 3x + 1, "a")
(Number field of degree 3 over QQ, a)

julia> K
Number field with defining polynomial x^3 + 3*x + 1
  over rational field
```
