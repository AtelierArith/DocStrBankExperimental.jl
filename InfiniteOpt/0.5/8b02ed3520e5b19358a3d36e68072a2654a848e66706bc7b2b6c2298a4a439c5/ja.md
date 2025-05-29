```
has_supports(pref::DependentParameterRef)::Bool
```

`pref`がサポートを持っている場合はtrueを返し、そうでない場合はfalseを返します。

**例**

```julia-repl
julia> has_supports(x[1])
true
```
