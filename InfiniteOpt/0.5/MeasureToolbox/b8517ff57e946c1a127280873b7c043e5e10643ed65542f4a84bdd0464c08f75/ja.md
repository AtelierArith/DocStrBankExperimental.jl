```
clear_uni_integral_defaults()::Nothing
```

一変数積分のキーワード引数のデフォルトを初期状態にクリアしてリセットします。

**例**

```julia-repl
julia> uni_integral_defaults()
Dict{Symbol,Any} with 3 entries:
  :new_kwarg             => true
  :num_supports          => 5
  :eval_method           => Quadrature()

julia> clear_uni_integral_defaults()

julia> uni_integral_defaults()
Dict{Symbol,Any} with 1 entry:
  :eval_method => Automatic()
```
