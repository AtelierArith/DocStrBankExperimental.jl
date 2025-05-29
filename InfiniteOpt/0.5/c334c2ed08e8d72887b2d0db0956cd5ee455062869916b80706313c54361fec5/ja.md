```
set_derivative_method(pref::DependentParameterRef, 
                      method::NonGenerativeDerivativeMethod)::Nothing
```

`pref`に関して取られる導関数の評価方法`method`を指定します。`method`が生成的である場合（すなわち、追加のサポートの定義を必要とする場合）はエラーになります。

**例**

```julia-repl
julia> set_derivative_method(d, FiniteDifference())

```
