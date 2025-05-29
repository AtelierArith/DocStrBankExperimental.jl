```
derivative_method(pref::IndependentParameterRef)::AbstractDerivativeMethod
```

`pref`が導関数のオペレーターパラメータとして使用されるときに採用される数値導関数評価メソッドを返します。

**例**

```julia-repl
julia> derivative_method(pref) 
FiniteDifference(Backward, true)
```
