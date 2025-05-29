```
update_start!(partable::AbstractParameterTable, fit::SemFit)
update_start!(partable::AbstractParameterTable, model::AbstractSem, start_val; kwargs...)
```

`fit` または `start_val` から `partable` の `:start` 列に初期値を書き込みます。

# 引数

  * `start_val`: 初期値のベクトルまたは `model` から初期値を計算する関数
  * `kwargs...`: `start_val` に渡される引数
