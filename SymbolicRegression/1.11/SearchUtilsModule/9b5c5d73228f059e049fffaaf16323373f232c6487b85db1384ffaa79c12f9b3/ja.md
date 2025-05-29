```
RuntimeOptions{PARALLELISM,DIM_OUT,RETURN_STATE,LOGGER} <: AbstractRuntimeOptions
```

`equation_search` に直接渡される検索のためのパラメータであり、`Options` 内で設定されるのではありません。これは、処理および検索の期間に関連するパラメータと、検索のハイパーパラメータ自体に関するパラメータを区別するためです。
