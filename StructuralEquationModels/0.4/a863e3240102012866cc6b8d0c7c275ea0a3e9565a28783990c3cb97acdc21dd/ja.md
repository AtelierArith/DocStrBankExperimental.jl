```
se_bootstrap(sem_fit::SemFit; n_boot = 3000, data = nothing, kwargs...)
```

ブートストラップ標準誤差を返します。単一モデルにのみ対応しています。

# 引数

  * `n_boot`: ブートストラップサンプルの数
  * `data`: サンプリングするデータ。`sem_fit`のデータと異なる場合のみ必要です
  * `kwargs...`: `replace_observed`に渡されます
