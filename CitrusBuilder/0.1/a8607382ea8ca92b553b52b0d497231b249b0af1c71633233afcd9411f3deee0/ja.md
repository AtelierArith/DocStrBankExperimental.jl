```
has_attributes(question::Question)
```

[`Question`](@ref) に属性があるかどうかを確認します。

# 例

```julia-repl
julia> q = numerical_input("q1", "An input")
julia> has_attributes(q)
false
```

```julia-repl
julia> q = numerical_input("q1", "An input with attributes", minimum=0, maximum=10)
julia> has_attributes(q)
true
```
