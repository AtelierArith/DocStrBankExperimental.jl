```
loginputs(instance::MLFlow, run_id::String; datasets::Array{DatasetInput})
loginputs(instance::MLFlow, run::Run; datasets::Array{DatasetInput})
```

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `run_id`: このフィールドの下にログを記録するために必要な [`Run`](@ref) のID。
  * `datasets`: ログを記録するための [`DatasetInput`](@ref) のコレクション。

# 戻り値

成功した場合は `true`。それ以外の場合は例外を発生させます。
