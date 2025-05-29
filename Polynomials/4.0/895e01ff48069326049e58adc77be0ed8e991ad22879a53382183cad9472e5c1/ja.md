```
poles(pq::AbstractRationalFunction{T};
    method=:numerical, multroot_method=nothing, kwargs...) where {T}
```

有理関数 `p/q` に対して、まず通常形に簡約し、次に結果の分母の根と重複度を見つけます。

  * `method` は `lowest_terms` に渡すために使用されます
  * `multroot_method` は `multroot` のメソッド引数に渡され、`:direct`（より速いデフォルト）または `:iterative`（より遅く、場合によってはより堅牢な代替）を指定できます。デフォルトは `Big` 値の場合を除いて `:direct` です。
