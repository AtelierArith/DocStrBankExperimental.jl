```
algebraic_closure(::QQField)
```

有理数体の代数的閉包を表す体を返します。

# 例

```jldoctest
julia> K = algebraic_closure(QQ)
有理数体の代数的閉包

julia> sqrt(K(2))
x^2 - 2 の根 1.41421
```
