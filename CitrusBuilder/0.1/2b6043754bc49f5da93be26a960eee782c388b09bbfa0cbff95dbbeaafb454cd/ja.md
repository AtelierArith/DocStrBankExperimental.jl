```
attributes(question::Question)
```

[`Question`](@ref)の属性を取得します。

# 例

```julia-repl
julia> q = numerical_input("q1", "数値入力", minimum=0, maximum=10)
julia> attributes(q)
Dict{String, Any} with 2 entries:
  "min_num_value_n" => 0
  "max_num_value_n" => 10
```
