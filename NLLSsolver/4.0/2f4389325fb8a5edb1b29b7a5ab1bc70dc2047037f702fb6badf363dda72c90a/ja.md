```
NLLSsolver.ndeps(mycost::AbstractCost)
```

`mycost`が依存する変数の数を返します。返り値は静的整数でなければなりません。

# 例

2つの変数の関数であるコスト関数`MyCost <: AbstractCost`の場合、ユーザーは次の関数を定義する必要があります。

```julia
    NLLSsolver.ndeps(::MyCost) = static(2)
```

!!! 注     必要なユーザー特化API関数。
