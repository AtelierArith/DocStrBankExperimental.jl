```
p8est_ghost_exchange_data_begin(p8est_, ghost, ghost_data)
```

非同期のゴーストデータ交換をメッセージを投稿することで開始します。引数は[`p8est_ghost_exchange_data`](@ref)と同じです。戻り値の型は常に非NULLであり、交換を完了するために[`p8est_ghost_exchange_data_end`](@ref)に渡す必要があります。ゴーストデータは完了するまでアクセスしてはいけません。

### パラメータ

  * `ghost_data`:[in,out] 完了呼び出しまで生存している必要があります。

### 戻り値

進行中のメッセージのための一時ストレージ。

### プロトタイプ

```c
p8est_ghost_exchange_t *p8est_ghost_exchange_data_begin (p8est_t * p8est, p8est_ghost_t * ghost, void *ghost_data);
```
