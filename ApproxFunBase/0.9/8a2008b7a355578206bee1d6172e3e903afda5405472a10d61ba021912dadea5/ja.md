```
setdomain(f::Fun, d::Domain)
```

`f`を`domain`に射影します。

!!! note
    新しい関数は元の関数と異なる場合があります。係数は変更されません。


# 例

```jldoctest
julia> f = Fun(x->x^2);

julia> domain(f) == ChebyshevInterval()
true

julia> g = setdomain(f, 0..1);

julia> domain(g) == 0..1
true

julia> coefficients(f) == coefficients(g)
true
```
