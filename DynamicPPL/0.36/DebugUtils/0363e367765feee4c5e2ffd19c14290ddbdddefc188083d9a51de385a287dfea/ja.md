```
check_model([rng, ]model::Model; kwargs...)
```

`model`が有効であることを確認し、潜在的な問題について警告します。

サポートされているキーワード引数や実行されるチェックの種類の詳細については、[`check_model_and_trace`](@ref)を参照してください。

# 戻り値

  * `issuccess::Bool`: モデルチェックが成功したかどうか。
