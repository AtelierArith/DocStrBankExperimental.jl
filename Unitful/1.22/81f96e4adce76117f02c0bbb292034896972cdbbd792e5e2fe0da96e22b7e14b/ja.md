```
ustrip(x::Number)
ustrip(x::Quantity)
```

単位の前にある数値を返します。`x`の値は、次元のない量の場合、単位の前にある数値と異なる場合があります。例えば、`1m/mm != 1`です。詳細は[`uconvert`](@ref)および以下の例を参照してください。単位が削除されるため、情報が失われる可能性があり、注意して使用する必要があります — より安全な代替手段として`ustrip(u,x)`を参照してください。

```jldoctest
julia> ustrip(2u"μm/m") == 2
true

julia> uconvert(NoUnits, 2u"μm/m") == 2//1000000
true
```
