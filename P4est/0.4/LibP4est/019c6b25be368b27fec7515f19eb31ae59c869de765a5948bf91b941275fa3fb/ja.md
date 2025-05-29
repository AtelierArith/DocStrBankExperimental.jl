```
p8est_ghost_exchange_custom_levels_begin(p8est_, ghost, minlevel, maxlevel, data_size, mirror_data, ghost_data)
```

非同期のゴーストデータ交換をメッセージを投稿することで開始します。引数は [`p8est_ghost_exchange_custom_levels`](@ref) と同じです。戻り値の型は常に非NULLであり、交換を完了させるために [`p8est_ghost_exchange_custom_levels_end`](@ref) に渡す必要があります。ゴーストデータは完了前にアクセスしてはいけません。ミラーデータは、この関数が返された直後に安全に破棄できます。なぜなら、それは内部送信バッファにコピーされるからです。

### パラメータ

  * `mirror_data`:[in] もはや生存している必要はありません。
  * `ghost_data`:[in,out] 完了呼び出しまで生存している必要があります。

### 戻り値

進行中のメッセージのための一時的なストレージ。

### プロトタイプ

```c
p8est_ghost_exchange_t *p8est_ghost_exchange_custom_levels_begin (p8est_t * p8est, p8est_ghost_t * ghost, int minlevel, int maxlevel, size_t data_size, void **mirror_data, void *ghost_data);
```
