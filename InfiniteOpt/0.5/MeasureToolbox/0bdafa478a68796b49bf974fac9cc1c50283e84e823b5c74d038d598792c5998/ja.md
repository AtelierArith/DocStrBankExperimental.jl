```
clear_multi_integral_defaults()::Nothing
```

多変数積分のキーワード引数のデフォルトを初期状態にクリアしてリセットします。

**例**

```julia-repl
julia> multi_integral_defaults()
Dict{Symbol,Any} with 3 entries:
  :new_kwarg             => true
  :num_supports          => 5
  :eval_method           => Automatic()

julia> clear_multi_integral_defaults()

julia> multi_integral_defaults()
Dict{Symbol,Any} with 1 entry:
  :eval_method => Automatic()
```
