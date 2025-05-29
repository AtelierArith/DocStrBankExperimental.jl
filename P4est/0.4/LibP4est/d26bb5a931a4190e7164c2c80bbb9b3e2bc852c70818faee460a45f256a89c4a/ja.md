```
p4est_reset_data(p4est_, data_size, init_fn, user_pointer)
```

ユーザーポインタと要素データをリセットします。データサイズが変更されると、四分木データは解放され、新たに割り当てられます。初期化コールバックは各四分木で呼び出されます。古いuser_dataの内容は無視されます。

### パラメータ

  * `data_size`:[in] 各四分木のデータサイズで、ゼロにすることもできます。その場合、user*data*poolはNULLに設定されます。
  * `init_fn`:[in] 自動的に割り当てられたuser_dataを初期化するためのコールバック関数。NULLである可能性があります。
  * `user_pointer`:[in] init*fnが最初に呼び出される前に、`p4est`のuser*pointerメンバーに割り当てます。

### プロトタイプ

```c
void p4est_reset_data (p4est_t * p4est, size_t data_size, p4est_init_t init_fn, void *user_pointer);
```
