```
has_supports(prefs::AbstractArray{<:DependentParameterRef})::Bool
```

`prefs`がサポートを持っている場合はtrueを返し、そうでない場合はfalseを返します。すべての無限依存パラメータが同じオブジェクトからでない場合はエラーが発生します。

**例**

```julia-repl
julia> has_supports(x)
true
```
