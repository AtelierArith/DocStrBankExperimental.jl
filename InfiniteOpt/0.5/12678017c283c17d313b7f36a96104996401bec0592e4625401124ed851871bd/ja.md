```
used_by_derivative(fref::ParameterFunctionRef)::Bool
```

`fref` が導関数によって使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_derivative(vref)
true
```
