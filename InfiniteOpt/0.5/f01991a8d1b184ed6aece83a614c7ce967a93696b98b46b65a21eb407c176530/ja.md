```
is_used(pref::Union{IndependentParameterRef, FiniteParameterRef})::Bool
```

`pref`がモデルで使用されている場合はtrueを返し、そうでない場合はfalseを返します。

**例**

```julia-repl
julia> is_used(t)
true
```
