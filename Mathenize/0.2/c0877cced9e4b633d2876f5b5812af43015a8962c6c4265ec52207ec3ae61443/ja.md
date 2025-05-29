```
calculate(math::String, print_info::Bool=false)
```

計算された値を文字列で返します。

# 引数

  * `math::String` 数学演算。
  * `print_info::Bool` 計算中に何が起こったかのログを表示します。

# 例

```julia-repl
julia> calculate("sqrt(complex(-90)) + 10im")
0.0 + 19.486832980505138im
```
