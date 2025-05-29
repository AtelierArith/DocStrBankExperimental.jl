```
QQBarField <: Field
QQBarFieldElem <: FieldElem
```

有理数 $\mathbb Q$ の代数的閉包 $\overline{\mathbb Q}$ とその要素。これはシングルトン型であり、このフィールドのユニークなグローバルインスタンスが存在し、`algebraic_closure(QQ)` を介して取得できます。

```jldoctest
julia> K = algebraic_closure(QQ)
Algebraic closure of rational field

julia> sqrt(K(2))
Root 1.41421 of x^2 - 2

julia> QQBar(2//3)
Root 0.666667 of 3x - 2

julia> sinpi(QQBar(2//3))
Root 0.866025 of 4x^2 - 3
```
