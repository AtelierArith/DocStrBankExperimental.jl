```
misclassification(results::AbstractVector{Tuple{<:Number,<:Number}})
```

誤分類された例の数を返します。つまり、`results`に一致しないエントリを持つタプルがいくつあるかです。

# 引数

  * `results<:AbstractVector{<:Tuple{Number,Number}}`: 各タプルが`Tuple{expected_output, actual_output}`の形式であるタプルのベクターです。
