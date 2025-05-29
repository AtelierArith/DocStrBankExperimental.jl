```
checkpoint(cp::Link, key::Symbol, args...)
```

チェックポイントを取るようにチェックポイントアクターに指示します。

# 引数

  * `cp::Link`: [`Link`](@ref) チェックポイントアクターへのリンク、
  * `key::Symbol`: チェックポイントのキー、
  * `args...`: チェックポイントに保存する変数、
  * `level::Int=1`: チェックポイントレベル。
