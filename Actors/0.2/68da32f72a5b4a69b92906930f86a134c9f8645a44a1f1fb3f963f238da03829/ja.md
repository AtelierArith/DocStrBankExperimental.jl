```
restore(cp::Link; key::Symbol)
```

チェックポイントを取得したアクターに、最後に取得したチェックポイントを復元するように指示します。

# 引数

  * `cp::Link`:  [`Link`](@ref) チェックポイントアクターへのリンク、
  * `key::Symbol`: チェックポイントキー、
  * `level::Int=1`: 復元するチェックポイントレベル。
