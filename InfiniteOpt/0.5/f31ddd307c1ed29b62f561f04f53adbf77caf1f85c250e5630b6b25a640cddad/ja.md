```
JuMP.set_value(pref::FiniteParameterRef, value::Real)::Nothing
```

`pref`の値を設定しますが、それが有限パラメータである限りです。無限パラメータの場合はエラーになります。

**例**

```julia-repl
julia> set_value(cost, 27)

julia> value(cost)
27.0
```
