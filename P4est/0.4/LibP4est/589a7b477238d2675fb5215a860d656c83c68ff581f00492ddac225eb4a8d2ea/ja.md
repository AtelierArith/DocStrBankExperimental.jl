```
p4est_ghost_exchange_custom_begin(p4est_, ghost, data_size, mirror_data, ghost_data)
```

非同期のゴーストデータ交換をメッセージを投稿することで開始します。引数は[`p4est_ghost_exchange_custom`](@ref)と同じです。戻り値の型は常に非NULLであり、交換を完了するために[`p4est_ghost_exchange_custom_end`](@ref)に渡す必要があります。ゴーストデータは完了するまでアクセスしてはいけません。ミラーデータは、この関数が返された直後に安全に破棄できます。なぜなら、それは内部送信バッファにコピーされるからです。

### パラメータ

  * `mirror_data`:[in] これ以上生存する必要はありません。
  * `ghost_data`:[in,out] 完了呼び出しまで生存する必要があります。

### 戻り値

進行中のメッセージのための一時ストレージ。

### プロトタイプ

```c
p4est_ghost_exchange_t *p4est_ghost_exchange_custom_begin (p4est_t * p4est, p4est_ghost_t * ghost, size_t data_size, void **mirror_data, void *ghost_data);
```
