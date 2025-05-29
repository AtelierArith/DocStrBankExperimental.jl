```
mean_squared_error(results::AbstractVector{Tuple{<:Number,<:Number}})
```

`results`の平均二乗誤差を返します。

# 引数

  * `results<:AbstractVector{<:Tuple{Number,Number}}`: 各タプルが`Tuple{expected_output, actual_output}`の形式であるタプルのベクトル。
